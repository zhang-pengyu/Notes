### Notes on opencv installation (CUDA and CUDNN needed)
## Download 
Download opencv and corresponding opencv-contrib via \
[[opencv4.5.0]](https://github.com/opencv/opencv/archive/4.5.0.zip)\
[[opencv-contrib4.5.0]](https://github.com/opencv/opencv_contrib/archive/4.5.0.zip)\
the mirror of them are provided by Gitee for Chinese users.\
[[opencv4.5.0]](https://gitee.com/mirrors/opencv/repository/archive/4.5.0.zip)\
[[opencv-contrib4.5.0]](https://gitee.com/mirrors/opencv_contrib/tree/4.5.0)\

In case some files fail to download, we download it manually. such as ippicv, boostdesc and vgg and put it into corresponding folders via cmake files\
~/opencv/3rdparty/ippicv/ippicv.cmake\
ln42 change to 'file:/media/zpy/Data2/Ubuntu_support/Ubuntu_support/opencv_4.5.0_install/opencv_download/'
~/opencv_contrib/modules/xfeatures2d/cmake/download_boostdesc.cmake\
~/opencv_contrib/modules/xfeatures2d/cmake/download_vgg.cmake\

## Install 
sudo apt-get install build-essential \
sudo apt-get install cmake git libgtk2.0-dev pkg-config libavcodec-dev libavformat-dev libswscale-dev ffmpeg\
sudo apt-get install python-dev python-numpy libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libdc1394-22-dev\
sudo apt-get install libgstreamer-plugins-base1.0-dev
sudo add-apt-repository "deb http://security.ubuntu.com/ubuntu xenial-security main"\
sudo apt update\
sudo apt install libjasper1 libjasper-dev\

cd $your opencv folder$\
mkdir build\
cd build \

cmake -D WITH_CUDA=ON\
-D BUILD_opencv_world=ON\
-D CMAKE_BUILD_TYPE=RELEASE\
-D OPENCV_ENABLE_NONFREE=ON\
-D OPENCV_EXTRA_MODULES_PATH=/home/zpy/opencv_contrib/modules\
-D BUILD_TIFF=ON\
-D BUILD_opencv_python2=OFF\
-D BUILD_EXAMPLES=ON\
-D PYTHON3_EXCUTABLE=/home/zpy/anaconda3/envs/MGVT/bin/python3.6m\
-D PYTHON3_INCLUDE_DIR=/home/zpy/anaconda3/envs/MGVT/include/python3.6m\
-D PYTHON3_LIBRARY=/home/zpy/anaconda3/envs/MGVT/lib/libpython3.6m.a\
-D PYTHON_NUMPY_PATH=/home/zpy/anaconda3/envs/MGVT/lib/python3.6/site-packages ..

cmake -D WITH_CUDA=ON\
-D BUILD_opencv_world=ON\
-D CMAKE_BUILD_TYPE=RELEASE\
-D OPENCV_ENABLE_NONFREE=ON\
-D OPENCV_EXTRA_MODULES_PATH=/home/zpy/opencv_contrib/modules\
-D BUILD_TIFF=ON\
-D BUILD_opencv_python2=OFF\
-D BUILD_opencv_python3=ON\
-D BUILD_EXAMPLES=ON\
-D PYTHON3_EXCUTABLE=/home/zpy/anaconda3/envs/MGVT/bin/python3.6m\
-D PYTHON3_INCLUDE_DIR=/home/zpy/anaconda3/envs/MGVT/include/python3.6m\
-D PYTHON3_LIBRARY=/home/zpy/anaconda3/envs/MGVT/lib/libpython3.6m.a\
-D PYTHON3_NUMPY_INCLUDE_DIRS=/home/zpy/anaconda3/envs/MGVT/lib/python3.6/site-packages/numpy\
-D PYTHON3_PACKAGES_PATH=/home/zpy/anaconda3/envs/MGVT/lib/python3.6/site-packages ..

make -j8 \
sudo make install \

##Copy opencv module into anaconda
sudo cp /usr/local/lib/python3.6/dist-packages/cv2 $your anaconda envs$/lib/python3.6/site-packages\

If you have any questions, feel free to contact [[pyzhang@mail.dlut.edu.cn]](pyzhang@mail.dlut.edu.cn)\
