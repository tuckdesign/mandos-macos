# mandos-macos
This repository gives a port of Mandos Server to MacOs. Base version of Mandos Server used for this was 1.7.20.

## Requirements

You need to instal gpg, PyGobject with homebrwe and python-zeroconf (v0.19.1) that you need to install manually, because latest version dropped support for Python 2.

## Installation

### Client
On client side install mandos-client. I am using deb file from repository on Ubuntu 16.04. I guess this and later versions should also work (earlier versions don't).
In scripts.diff, replace enp0s3 with network interface name on your client.
Edit files in /usr/share/initramfs-tools on client side using .diff files on this repository.
Generate key: sudo mandos-keygen --password and copy it to server in /etc/mandos/clients.conf
Run sudo update-initramfs -k all -u

### Server
On MacOs, after installing brew packages copy mandos file to /usr/local/bin and .conf files to /etc/mandos/ folder.
Create /usr/local/var/lib/mandos folder.

You can either run it manually or create launchd service by copying com.tuckdesign.mandos.plist into /Library/LaunchDaemons on your Mac and loading it with sudo launchctl load /Library/LaunchDaemons/com.tuckdesign.mandos.plist. If password is not received you can try to stop service (it will restart automatically).

