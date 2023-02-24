# 1. windows terminal + ubuntu

https://ubuntu.com/tutorials/install-ubuntu-on-wsl2-on-windows-11-with-gui-support#1-overview

```bash
#cmd in admin mode

wsl --install
# restart

wsl --list --online
wsl --install -d Ubuntu-20.04
# restart

wsl cat /proc/version
wsl --update
wsl -l -v 

```

wsl versions management

https://pureinfotech.com/upgrade-wsl2-wsl1-windows-10/

https://pureinfotech.com/install-windows-subsystem-linux-2-windows-10/



# 2. NVIDIA driver

Quadro - P620

# 3. CUDA 11.6(For NVIDIA Quadro P620) 

https://developer.nvidia.com/cuda-11-6-0-download-archive?target_os=Linux&target_arch=x86_64&Distribution=WSL-Ubuntu&target_version=2.0&target_type=deb_local

## 3.1 ignore wsl - ubuntu

```bash
sudo apt-key del 7fa2af80

# wget https://developer.download.nvidia.com/compute/cuda/repos/ubuntu2004/x86_64/cuda-ubuntu2004.pin
sudo mv cuda-ubuntu2004.pin /etc/apt/preferences.d/cuda-repository-pin-600
# wget https://developer.download.nvidia.com/compute/cuda/11.6.0/local_installers/cuda-repo-ubuntu2004-11-6-local_11.6.0-510.39.01-1_amd64.deb
sudo dpkg -i cuda-repo-ubuntu2004-11-6-local_11.6.0-510.39.01-1_amd64.deb
sudo apt-key add /var/cuda-repo-ubuntu2004-11-6-local/7fa2af80.pub
sudo apt-get update
sudo apt-get -y install cuda

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.6/lib64
export PATH=$PATH:/usr/local/cuda-11.6/bin
export CUDA_HOME=$CUDA_HOME:/usr/local/cuda-11.6
```



## 3.2 Ensure wsl2

```bash
wget https://developer.download.nvidia.com/compute/cuda/repos/wsl-ubuntu/x86_64/cuda-wsl-ubuntu.pin
sudo mv cuda-wsl-ubuntu.pin /etc/apt/preferences.d/cuda-repository-pin-600
wget https://developer.download.nvidia.com/compute/cuda/11.6.0/local_installers/cuda-repo-wsl-ubuntu-11-6-local_11.6.0-1_amd64.deb
sudo dpkg -i cuda-repo-wsl-ubuntu-11-6-local_11.6.0-1_amd64.deb
sudo apt-key add /var/cuda-repo-wsl-ubuntu-11-6-local/7fa2af80.pub
sudo apt-get update
sudo apt-get -y install cuda


export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-11.6/lib64
export PATH=$PATH:/usr/local/cuda-11.6/bin
export CUDA_HOME=$CUDA_HOME:/usr/local/cuda-11.6
```



# 4. Linux Terminal envs

```bash
sudo apt install build-essential
sudo apt install python3.x
```



# 5.Miniconda 

```bash


bash miniconda - python3.x
bash

conda install pytorch torchvision torchaudio pytorch-cuda=11.6 -c pytorch -c nvidia
pip install jupyter d2l rise
pip install torch==1.12.1+cu116 torchvision==0.13.1+cu116 torchaudio==0.12.1 --extra-index-url https://download.pytorch.org/whl/cu116

```

