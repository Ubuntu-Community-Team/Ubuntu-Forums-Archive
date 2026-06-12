---
title: "Skype 2.1.0.47 and Ubuntu 9.04 (jaunty)"
date: 2010-01-05
forum: General Help
---

### Post by Noma on 2010-01-05
Ubuntu lovers!

For those who can not make skype work with mic.

I looked through numerous treads about skype mic (usb web cam) problem and did not find any answer, i even did screw my installation and have to reinstall, playing with pulse, alsa, mixers does not give anything.

&#1054;&#1082;. It was really simple. It worked for me! All you have to do is to build last alsa drivers and utils and install.

Thanx to Stéphane        Gaudreaultand his manual for alsa upgrade at [HTML]http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/[/HTML]

1) Stop alsa ```
sudo /etc/init.d/alsa-utils stop  
```
2) Install necessary tools ```
sudo apt-get -y install build-essential ncurses-dev gettext xmlto
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev
```
3) Download last alsa (i used 1.0.22 although the newest driver there is 2.0.22.1) to your home ```
cd ~
rm -rf ~/alsa* ~/.pulse*
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.22.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.22.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.22.tar.bz2
```
4) Get ready for compilation ```
sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/alsa* .
```
5) Unpack ```
sudo tar xjf alsa-driver*
sudo tar xjf alsa-lib*
sudo tar xjf alsa-utils*
```
6) Compile alsa driver ```
cd alsa-driver*
sudo ./configure
sudo make
sudo make install
```
7) Compile alsa-lib ```
cd ../alsa-lib*
sudo ./configure
sudo make
sudo make install
```
8) Compile alsa-utils ```
cd ../alsa-utils*
sudo ./configure
sudo make
sudo make install
```
9) Check if you have no erros during last ./configure and in case you do have this ```
checking form.h presence... yes
checking for form.h... yes
checking for new_panel in -lpanelw... no
configure: error: panelw library not found 
``` then ```
sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so
``` and restart with ```
sudo ./configure
```
10) Now you don't need any of that ```
rm -f ~/alsa-driver*
rm -f ~/alsa-lib*
rm -f ~/alsa-utils*
```
11) Reboot you Ubuntu-megapower-machine  and check if you have last alsa ```
cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.22.
Compiled on Jan 5 2010 for kernel 2.6.28-15-generic (SMP).
```
12) run ```
sudo alsaconf
``` and OK when script asks.
13) In alsamixer enable (unmute) all switches and set volume to medium for all channels except for those that say "boost"
14) In System/Properties/Volume control choose your device for recording.
15) ENJOY!

Me@Twitter: [HTML]http://twitter.com/aladin_nv[/HTML]

---

### Post by Noma on 2010-01-05
Guys, seems I've had double trouble. First my chip is ALC889A. That's why there was no sound, because of the outdated drivers. Building new ones helped the system to see my usb mike properly. But still I had problem with simultanious playback from skype and totem for instance.

Then I completely removed pulseaudio and everything works FINE now!

Try that if nothing mentioned above helps.

---

