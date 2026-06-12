---
title: "Suddenly no internet connection?"
date: 2012-02-26
forum: General Help
---

### Post by Hellageddon on 2012-02-26
Well, I am in a terrible situation:
My startx won't launch but more important now is, I suddenly have no internet connection (via router).

I don't know why, but here are my latest commands, if it might help:

```

startx
iwconfig
clear
ifconfig
clear
ifconfig wlan0 off
ping google.com
lspci
clear
ping google.com
sudo /sbin/ldconfig
sudo updatedb
ifconfig
reboot
startx
cd /etc/x11
cd /etc
ls
cd x11
cd X11
ls
clear
cd /
ls
sudo apt-get remove purge nvidia*
sudo apt-get purge nvidia*
startx
rm /etc/X11/xorg.conf
whereis xorg.conf
startx
reboot
echo "blacklist nouveau" >> /etc/modprobe.d/blacklist.conf
exit
sudo /etc/init.d/gdm stop
startx
lspci
reboot
sudo -i
login
apt-get purge x11-xserver-utils
apt-get purge xserver-common
apt-get purge xserver-xorg-core
apt-get purge xserver-xorg-dev
apt-get purge xserver-xorg-input-all
apt-get purge xserver-xorg-input-evdev
apt-get install xserver-xorg
apt-get update
ping google.com
ping google.com -c 3
host google.com
apt-get install dselect
apt-get upgrade
synaptic
startx
cd /etc/X11
ls
apt-get help
apt-get check
apt-get dselect-upgrade
startx
ifconfig
sudo /etc/init.d/networking restart
ps -a
shutdown -h 0


```

---

