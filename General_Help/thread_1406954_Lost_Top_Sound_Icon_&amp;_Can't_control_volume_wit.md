---
title: "Lost Top Sound Icon &amp; Can't control volume with Keyboard"
date: 2010-02-14
forum: General Help
---

### Post by sendblink23 on 2010-02-14
Hi my issue is as my Title "Lost Top Sound Icon & Can't control volume with Keyboard"

OS: Ubutnu 9.10 x64 - Karmic Koala

Lost the Top Panel Sound Icon, I even go to: System > Preferences > Sound

Message Pops Up: *Waiting for sound system to respond*

Funny thing I do get Ubuntu OS Audio sounds

Now as well I lost control of my Volume with my Keyboard, pretty sure it has to do with the same Sound icon in the Top panel that is missing

The only way I can control Audio is Manually using: gnome-alsamixer 0.9.7

It sucks big time, because I can't control my Audio when ever I need to mute it or upper/lower it through my keyboard fastly when needed...  having to manually opening an application to be able to change/control the Audio volume is a huge hassle for me


Any help? 

***Old Story of Today***
Originally from clean install I did had Ubuntu OS Audio.... upgraded to the latest updates and Lost all Audio in the Ubuntu OS, but all Flash Video sounds (youtube) worked perfectly fine...  so I my self tried to fix it doing this:

```
Getting the ALSA drivers from a *fresh* kernel

Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly.

(1) Remove these packages
Code:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils


(2) Reinstall those same packages
Code:

sudo apt-get install linux-sound-base alsa-base alsa-utils
[LIST][*]
VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
Code:

sudo apt-get install gdm ubuntu-desktop


(3) Reboot 
```

That messed up my Volume Controls of the Audio, Yes Keyboard & Sound Volume icon worked perfectly **VISUALLY** but not really making changes, I mean.... only still had Audio on Flash Videos, but I could not change the Audio Volume... visually it changed but Audio stayed the same - Yes STILL NO audio in the Ubuntu OS


So then I tried this:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge gstreamer0.10-pulseaudio vlc-plugin-pulse pulseaudio
```
**This above right here is where I got stuck right now, how I am currently as this Thread Issue I just Posted in the Very Top**.


This is on my new computer I just bought:

MOBO: MSI 770-C45 AM3
CPU: AMD Phenom ii X4 965BE C3 @ 3.40Ghz
RAM: 8gb (4 x 2gb) DDR3-1333 @ 800Mhz
GFX: ATI Radeon HD 4650 1gb DDR2 PCI-e
Optical Drive: LG DVD-RW
HDD: 1TB Hitachi Deskstar 7200rpm
CPU Cooling: Corsair H50 Push/Pull
Case Cooling: 1 x 120mm + 3 x 80mm

---

### Post by sendblink23 on 2010-02-14
Any suggestions?

I want to try this...  

```
sudo aptitude install libdns53 libdns53 ureadahead alsa-oss alsa-base alsa-tools alsa-tools-gui alsa-utils alsa-oss linux-sound-base asoundconf-gtk cabextract flashplugin-installer freepats gnome-alsamixer gsfonts-x11 gstreamer0.10-ffmpeg libesd-alsa0 gnome-alsamixer gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs java-common lib32asound2 lib32bz2-1.0 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 liba52-0.7.4 libao2 libass3 libaudclient2 libaudcore1 libaudid3tag2 libaudio2 libaudutil1 libavcodec52 libavformat52 libavutil49 libbinio1ldbl libbio2jack0 libbio2jack0-dev libcdaudio1 libcddb2 libcelt0 libdc1394-22 libdca0 libdirac0c2a libdvbpsi5 libdvdnav4 libdvdread4 libebml0 libenca0 libfaac0 libfaad0 libffado1 libfftw3-3 libfluidsynth1 libfreebob0 libftgl2 libgconfmm-2.6-1c2 libglademm-2.4-1c2a libglew1.5 libgsm1 libid3tag0 libiptcdata0 libiso9660-5 libjack-dev libjack0 libjack0 liblash2 liblua5.1-0 libmad0 libmatroska0 libmcs1 libmimic0 libmjpegtools-1.9 libmms0 libmodplug0c2 libmowgli1 libmp3lame0 libmp4v2-0 libmpcdec3 libmpeg2-4 libofa0 libpostproc51 libprojectm-data libprojectm2 libquicktime1 libreadline5 libresid-builder0c2a libsad2 libschroedinger-1.0-0 libsdl1.2debian-all libsidplay1 libsidplay2 libsoundtouch1c2 libswscale0 libtwolame0 libvcdinfo0 libvlc2 libvlccore2 libwildmidi0 libx264-67 libxml++2.6-2 libxvidcore4 nspluginwrapper odbcinst1debian1 sun-java6-bin sun-java6-jre sun-java6-plugin ttf-dejavu ttf-dejavu-extra ttf-liberation ttf-mscorefonts-installer ubuntu-restricted-extras unixodbc unrar vlc-data vlc-nox vlc-plugin-pulse linux-backports-modules-2.6.31-19-generic linux-backports-modules-alsa-2.6.31-19-generic linux-backports-modules-alsa-karmic-generic linux-backports-modules-headers-karmic-generic linux-backports-modules-karmic linux-backports-modules-karmic-generic linux-backports-modules-wireless-karmic-generic linux-headers-lbm-2.6.31-19-generic vlc
```

but I don't want to try it before anybody gives me some other terminal commands to try to fix my Lost Sound icon / Keyboard Sound controlling issue

---

### Post by sendblink23 on 2010-02-14
bump??? I need this fixed hugely

---

### Post by Youcandoit! on 2010-07-05
I've got this same issue. I have Ubuntu 10.04 netbook remix, and after reinstalling my netbook-launcher, I got exactly the same symptoms as you. Sound works, but can't control it. I have tried to purge and reinstall almost every sound related package, but nothing seems to work.

Perhaps there is something missing from /var/lib/alsa/asound.state or /usr/share/alsa/init/00main. I am starting to believe that it is not ALSA related problem at all.

---

### Post by Youcandoit! on 2010-07-05
Ok. Some new info. I suspect that the problem is with pulseaudio. System should run start-pulseaudio-x11 at startup. When I checked my running processes there is nothing pulseaudio related.

Then I tried to run start-pulseaudio-x11 from terminal, and this is the output: Failed to stat runtime directory /home/sini/.pulse/86126fb5399a1a6d6d1e6a5a4bdc2652-runtime.

Any Ubuntu gurus out there to solve this. I don't have a clue about next steps.

If your volume control has been disappeared from system panel, just reinstall indicator-sound with synaptic or apt-get.

Command: sudo apt-get install indicator-sound

---

### Post by Youcandoit! on 2010-08-11
I couldn't find any solution for this. Reinstalling alsa didn't help. I had to reinstall ubuntu. For me this broblem occoured after system crash, and my Acer Aspire One lost WLAN drivers at the same time.

---

