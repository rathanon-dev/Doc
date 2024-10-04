# Steps to Install the Latest NVIDIA Driver on Debian 12:
Install the GPG key to ensure the authenticity of the software being installed.
```bash
curl -fSsL https://developer.download.nvidia.com/compute/cuda/repos/debian12/x86_64/3bf863cc.pub | sudo gpg --dearmor | sudo tee /usr/share/keyrings/nvidia-drivers.gpg > /dev/null 2>&1
```
Add the NVIDIA repository to your system's sources list to access the latest driver versions. 
```bash
echo 'deb [signed-by=/usr/share/keyrings/nvidia-drivers.gpg] https://developer.download.nvidia.com/compute/cuda/repos/debian12/x86_64/ /' | sudo tee /etc/apt/sources.list.d/nvidia-drivers.list
```
Update your system's package list and upgrade to install the new driver version.
```bash
sudo apt update && sudo apt upgrade
```
### CUDA 12.4
Base Installer:
```bash
wget https://developer.download.nvidia.com/compute/cuda/12.4.0/local_installers/cuda-repo-debian12-12-4-local_12.4.0-550.54.14-1_amd64.deb
sudo dpkg -i cuda-repo-debian12-12-4-local_12.4.0-550.54.14-1_amd64.deb
sudo cp /var/cuda-repo-debian12-12-4-local/cuda-*-keyring.gpg /usr/share/keyrings/
sudo add-apt-repository contrib
sudo apt-get update
sudo apt-get -y install cuda-toolkit-12-4
```
Driver:
To install the open kernel module flavor:
```bash
sudo apt-get install -y nvidia-kernel-open-dkms
sudo apt-get install -y cuda-drivers# Doc
```
Reference [dcseng](https://github.com/blakeblackshear/frigate/discussions/10548)
