---
title: "How to get Perfect Sound on Ubuntu 10.04"
date: 2010-09-06
forum: General Help
---

### Post by Vigh on 2010-09-06
My contribution to the Ubuntu to community and documentation on how to set-up sound on Ubuntu 10.04.

Advanced Linux Sound Architecture for Ubuntu Comprehensive Guide by Ant 

Download required source code from 

[http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page) 

Required source packages include-
alsa-driver-1.0.23
alsa-lib-1.0.23
alsa-utils-1.0.23
alsa-plugins-1.0.23

Open terminal install autoconf and automake-

sudo apt-get install autoconf automake

Open terminal create new directory- 

sudo rm -rf /usr/src/alsa
sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa

Unpack  all folders using decompression manager to the /home/&#8221;username&#8221;/ (right click extract)

Move alsa folders to /usr/src/alsa in terminal-

sudo cp &#8211;r ~/alsa* /usr/src/alsa

In terminal type-

cd /usr/src/alsa/alsa-driver-1.0.23
sudo ./configure
sudo make
sudo make install

ALSA drivers will compile and install. In terminal type-

cd /usr/src/alsa/alsa-lib-1.0.23
sudo ./configure
sudo make
sudo make install

ALSA library dependencies will now compile and install. In terminal type-

cd /usr/src/alsa/alsa-utils-1.0.23
sudo apt-get -y install build-essential ncurses-dev gettext xmlto libasound2-dev
sudo apt-get -y install linux-headers-`uname -r` libncursesw5-dev

Required ncurses and linux headers will now install and prepare you for the alsa-utils installion. 

In terminal type-

sudo ln -s libpanelw.so.5 /usr/lib/libpanelw.so
sudo ln -s libformw.so.5 /usr/lib/libformw.so
sudo ln -s libmenuw.so.5 /usr/lib/libmenuw.so
sudo ln -s libncursesw.so.5 /lib/libncursesw.so

In terminal type-

sudo ./configure
sudo make
sudo make install

ALSA utils and dependencies will now be compiled and installed. In terminal type-

cd /usr/src/alsa/alsa-plugins-1.0.23
sudo ./configure
sudo make
sudo make install

ALSA plugins will now compile and install.
Reboot

Open terminal type-

sudo alsaconf

Follow prompts and select soundcard.
Reboot again.

sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter

Reboot again.

Your ALSA Sound System is now ready to use.

You may also want to install alsa-oss-1.0.17

Are a couple of other things needed I forgot to mention-

cd /etc/
sudo gedit asound.conf

Add the following lines and save-

pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}

Make sure your user account is part of the audio group and has audio permissions-
Go to system administration users/groups.

Need to install linux-backports via terminal to get microphone input working properly, may also need to add an options line into /etc/modprobe.d/alsa-base.conf.

Install by-
sudo apt-get install linux-backports-modules-alsa-lucid-generic for 10.04

---

### Post by robbiemacg on 2010-09-06
Getting the sound settings just so was a real challenge for me early on. I ended up muddling through the steps to get ALSA drivers, etc. installed and running correctly. 
This post might have been very valuable. I hope that it'll help others. Great job!

---

