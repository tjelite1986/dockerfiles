wget "https://dl.winehq.org/wine/wine-mono/9.0.0/wine-mono-9.0.0-x86.msi"

wine start wine-mono-9.0.0-x86.msi

****

sudo dpkg --add-architecture i386
sudo apt update
sudo wget -O /etc/apt/keyrings/winehq-archive.key https://dl.winehq.org/wine-builds/winehq.key
sudo wget -NP /etc/apt/sources.list.d/ https://dl.winehq.org/wine-builds/ubuntu/dists/jammy/winehq-jammy.sources
sudo apt update

sudo apt install --install-recommends winehq-stable
sudo apt install --install-recommends winehq-devel

wine --version


mkdir -p ~/myapp/prefix
export WINEPREFIX=$HOME/myapp/prefix
export WINEARCH=win32
export WINEPATH=$HOME/myapp
wineboot --init
winetricks

wineboot -u
wine uninstaller --list

