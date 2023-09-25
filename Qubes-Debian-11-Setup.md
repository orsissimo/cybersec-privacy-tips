# Qubes OS Setup for Ethereum Development

This guide will help you to set up your development environment in Qubes OS for Ethereum application development.

## TemplateVM:

First, update your system and install some necessary packages:

```bash
sudo apt-get update
sudo apt-get upgrade

sudo apt-get install build-essential vim emacs git python3 python3-pip default-jdk nodejs npm curl wget snapd qubes-snapd-helper
```

Optionally, you can also install `pipx`:

```bash
sudo apt-get pipx
```

## AppVM:

Now, inside your AppVM, install Node Version Manager (nvm), set the default version of Node.js, and install some global npm packages:

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash
source /home/user/.bashrc
nvm install node
nvm alias default node

sudo npm install -g yarn solc
```

Next, install [Foundry](https://getfoundry.sh/), a toolkit for Ethereum application development:

```bash
curl -L https://foundry.paradigm.xyz | bash
source /home/user/.bashrc
foundryup
```

If you are working with a React project, you might need to install these npm packages (not globally):

```bash
npm install create-react-app create-next-app truffle ganache-cli web3 ethers eslint prettier
```

### Python 3.9 Setup:

It is recommended to use Python 3.9. Install `python3-venv` and create a virtual environment:

```bash
sudo apt-get install python3-venv
mkdir venvs
python3 -m venv venvs/brownie-env
source venvs/brownie-env/bin/activate
deactivate
```

Then, install some necessary Python packages:

```bash
pip install eth-brownie web3 pytest requests termcolor
pip list
```

To uninstall all packages, you can use:

```bash
pip freeze | xargs pip uninstall -y
```

Finally, install some applications using Snap:

```bash
sudo snap install code --classic
sudo snap install gitkraken --classic
sudo snap install telegram-desktop
snap list
```

If you want to use Github Desktop:

```bash
sudo wget https://github.com/shiftkey/desktop/releases/download/release-3.1.1-linux1/GitHubDesktop-linux-3.1.1-linux1.deb
sudo apt-get install gdebi-core
sudo gdebi GitHubDesktop-linux-3.1.1-linux1.deb
```

If you want to use a VPN, I'd recommend to install OpenVPN and add it to path (`/usr/sbin` in the example):
```bash
sudo apt-get install openvpn
whereis protonvpn
nano ~/.bashrc
export PATH=$PATH:/usr/sbin
source ~/.bashrc
```
Now you can [configure ProtonVPN on top of OpenVPN](https://protonvpn.com/support/linux-openvpn/)

For other Snap applications, visit the [Snap Store](https://snapcraft.io/store).

```
Happy coding!
```
