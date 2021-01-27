Bootstrap: docker

From: nvcr.io/nvidia/pytorch:20.09-py3

%environment
#EXPOSE 8888
#EXPOSE 6006
#EXPOSE 8003
export CPLUS_INCLUDE_PATH=/usr/include/gdal
export C_INCLUDE_PATH=/usr/include/gdal

%post

apt-get -y update
apt-get install -y software-properties-common
apt-get -y update
add-apt-repository universe
add-apt-repository ppa:ubuntugis/ppa


apt-get -y install libglib2.0-0
apt-get -y install wget
apt-get -y install pv
apt-get -y install git
apt-get -y install libavcodec-dev libavformat-dev libswscale-dev
apt-get -y install libgstreamer-plugins-base1.0-dev libgstreamer1.0-dev
apt-get -y install libgtk-3-dev
apt-get -y install libpng-dev
apt-get -y install libjpeg-dev
apt-get -y install libopenexr-dev
apt-get -y install libtiff-dev
apt-get -y install libwebp-dev
apt-get -y install libhdf5-serial-dev
apt-get -y install screen
apt-get -y install ffmpeg --fix-missing

/opt/conda/bin/conda init bash
/opt/conda/bin/conda update -y python
/opt/conda/bin/conda install -y python=3.7.7
python3 -m pip install --upgrade pip 
python3 -m pip install --upgrade setuptools
pip3 install numpy
pip3 install matplotlib tqdm Pillow shapely opencv-python pandas scikit-learn imgaug imantics scipy scikit-image seaborn pandas
pip3 install netCDF4
pip3 install earthnet


#Install GDAL and python binding
apt-get install -y gdal-bin
apt-get install -y libgdal-dev
ogrinfo --version

#Add here the ogr version
pip3 install GDAL==2.4.2
pip3 install git+https://gitext.gfz-potsdam.de/danschef/geoarray.git
pip3 install git+https://gitext.gfz-potsdam.de/danschef/arosics.git
pip3 install sentinelsat sentinelhub Cartopy

#JupyterLab Set-up
/opt/conda/bin/conda install qt
/opt/conda/bin/conda install -y jupyter jupyterlab
pip3 install jupytext
pip3 install jupyter_tensorboard
pip3 install --upgrade jupyterlab-git
/opt/conda/bin/conda install -y nb_conda_kernels

#Create the conda environment for Tf_template named ENtf115py36
/opt/conda/bin/conda create --name ENtf115py36 python=3.6
/opt/conda/bin/conda activate ENtf115py36
pip3 install numpy matplotlib scipy sk-video ffmpeg opencv-python scikit-image h5py tensorflow-gpu==1.15 earthnet
/opt/conda/bin/conda install -y ipykernel


#Create the conda environment for PyTorch_template named ENpt16py38
/opt/conda/bin/conda create --name ENpt16py38 python=3.8.5
#SHELL ["conda", "run", "-n", "ENpt16py38", "/bin/bash", "-c"]
/opt/conda/bin/conda activate ENpt16py38
pip3 install --upgrade pip 
pip3 install --upgrade setuptools 
pip3 install numpy==1.19.2 
pip3 install torch==1.6.0 torchvision==0.7.0 pytorch-lightning==1.1.0
pip3 install matplotlib==3.3.2 tqdm Pillow shapely opencv-python pandas scikit-learn imgaug imantics scipy scikit-image seaborn pandas
pip3 install earthnet
/opt/conda/bin/conda install -y ipykernel
