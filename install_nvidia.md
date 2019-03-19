# Instalation CUDA 10 on UBUNTU 18.04
###### [robson85me](https://github.com/robson85m) create this page on March 19, 2019

___

If you have fresh install ubuntu don't do it

## Uninstall just nvidia-cuda-toolkit
```bash
sudo apt-get remove nvidia-cuda-toolkit #or
sudo apt-get remove --auto-remove nvidia-cuda-toolkit
sudo rm /etc/apt/sources.list.d/cuda*
sudo apt remove nvidia-*

```
delete folder cuda `rm -rf`
and delete line in  lines of the `~/.bashrc` file

___
## install driver nvidia ([link to askubunt](https://askubuntu.com/questions/1077061/how-do-i-install-nvidia-and-cuda-drivers-into-ubuntu))
```bash
sudo apt update

sudo apt-key adv --fetch-keys  http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/7fa2af80.pub

sudo bash -c 'echo "deb http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64 /" > /etc/apt/sources.list.d/cuda.list'

sudo apt update
sudo apt install nvidia-driver-410 # doesn't work with me
sudo apt install nvidia-driver-415
```
after instalation `reboot` check `nvidia-smi`
```bash


```
Download from [CUDA Toolkit Archive](https://developer.nvidia.com/cuda-toolkit-archive) package `deb`
```bash
sudo dpkg -i cuda-repo-ubuntu1804-10-0-local-10.0.130-410.48_1.0-1_amd64.deb
sudo apt-key add /var/cuda-repo-10-0-local-10.0.130-410.48/7fa2af80.pub
sudo apt-get update
sudo apt-get install cudavim -10-0

```
```bash

export PATH=/usr/local/cuda-10.0/bin${PATH:+:${PATH}}
export LD_LIBRARY_PATH=/usr/local/cuda-10.0/lib64{LD_LIBRARY_PATH:+:${LD_LIBRARY_PATH}}

source ~/.bashrc

```

Verificate `nvcc -V` should return

```bash
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2018 NVIDIA Corporation
Built on Sat_Aug_25_21:08:01_CDT_2018
Cuda compilation tools, release 10.0, V10.0.130
```
Login to [NVIDIA cudnn page](https://developer.nvidia.com/rdp/cudnn-archive) and download cudnn v7.4 for CUDA 10

```bash
cd ~/Downloads/
tar -xzvf cudnn-10.0-linux-x64-v7.4.1.5.tgz

sudo cp cuda/include/cudnn.h /usr/local/cuda/include
sudo cp cuda/lib64/libcudnn* /usr/local/cuda/lib64
sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*

```
