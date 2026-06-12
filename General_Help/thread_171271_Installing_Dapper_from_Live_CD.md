---
title: "Installing Dapper from Live CD"
date: 2006-05-06
forum: General Help
---

### Post by rcarring on 2006-05-06
I have the latest iso image of the 6.06 Beta. Since on my vm it takes ages to boot, is it possible to perform an upgrade installation using the cd when I have booted to the Breezy desktop that I have installed on my vm already?

If not, where can I find the *.deb packages on the cd for Open office 2.02 so that I can install Open office using alien?

Thanks

---

### Post by Sef on 2006-05-06
First **back up** your data.  Then you can update without using a cd as long as you have an internet connection.

Open a terminal

then 

sudo apt-get update

next

sudo apt-get dist-upgrade

Note: This has more likely to break your system than a clean install.

---

### Post by Ramses de Norre on 2006-05-06
First you'll need to do sudo gedit /etc/apt/sources.list and change in every line the word 'breezy' by 'dapper', then you can do sudo apt-get update && sudo apt-get dist-upgrade.

---

### Post by rcarring on 2006-05-06
I'll try this. Thanks.

---

### Post by rcarring on 2006-05-06
Here is a quick update of what happened:

1) Edited sources.list to change breezy to dapper
2) Ran the commands required
3) With my existing choices of programs installed (OOo 1.9, OOo 1.1.5, Gimp 2.2) it told me that 664 packages were going to be upgraded, 95 new packages were to be installed and it also uninstalled both versions of OOo and updated OOo to 2.02 version.
The download took 14 minutes, downloaded approx. 324MB of packages.
4) The install started. This took in total (apart from having to manually re-configure xserver-xorg using dbkg-reconfigure as root) over an hour or so. I answered "N" to each question where it said keep or replace a modified conf file, I think I should have said "Y" to the hal.conf as a few strings inside it don't appear to be recognized by the system -- I can't remember what they are.
5) After completing the install, I rebooted my VM, this was where X server got upset and insisted that device vmmouse did not exist (I think the dist-upgrade) removed it. Running dpkg-reconfigure xserver-xorg as root, aloowed me to reconfigure my Xserver and tell it what mouse etc to use. I ran startx as root, then logged out and ran startx as the user.

---
The display is lot snappier, I am very pleased with the updated interface.

---

### Post by ffferko on 2006-05-06
ALT+F2

gksudo "update-manager -d"

---

### Post by rcarring on 2006-05-06
At present the emulated ensoniq sound card is recognized but no driver is installed, I got the Device Manager applet working by running hald -daemon=yes but there doesn't seem to be a way to get it to install drivers for the sound card.

---

