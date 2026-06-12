---
title: "Sound problems on HP2133 with 10.4"
date: 2010-05-14
forum: General Help
---

### Post by Brissenden on 2010-05-14
I have upgraded my HP2133 netbook to 10.04, but find that I am now unable to get any sounds after the initial sign in. The sound preferences hardware tab initially shows the correct sound card, but this vanishes when I try to do anything eg listen to the radio / access youtube / skype. 

I have searched the web with no joy to find a solution, so have joined the forum to see if anyone can point me in the right direction.

---

### Post by demwz on 2010-05-16
add a line:
options snd-hda-intel model=mobile
to /etc/modprobe.d/alsa-base.conf

to make sure frontspeaker is unmuted use gnome-alsa-mixer

for me it works

---

### Post by Brissenden on 2010-05-22
This change has certainly helped - can play Youtube, BBC i player & Skype, but system is still randomly loosing details of the sound card (VT1708/A) and going silent. I then have to reboot to get the sound back. Can anyone give me any more suggestions?

---

### Post by Freefalldart on 2011-01-31
Upgrading to alsa 1.0.24 worked for me. Just download the AlsaUpgrade script from [here]("http://ubuntuforums.org/showthread.php?p=6589810"), edit it and change:

PACKAGE=1.0.23

setpack () {
DRIVER=alsa-driver-1.0.23
FIRMWARE=alsa-firmware-1.0.23
LIB=alsa-lib-1.0.23
PLUGINS=alsa-plugins-1.0.23
UTILS=alsa-utils-1.0.23
TOOLS=alsa-tools-1.0.23
OSS=alsa-oss-1.0.17

to

PACKAGE=1.0.24

setpack () {
DRIVER=alsa-driver-1.0.24
FIRMWARE=alsa-firmware-1.0.24.1
LIB=alsa-lib-1.0.24.1
PLUGINS=alsa-plugins-1.0.24
UTILS=alsa-utils-1.0.24.2
TOOLS=alsa-tools-1.0.24.1
OSS=alsa-oss-1.0.17

Then follow the instructions in the thread to upgrade Alsa.

---

### Post by lean-mini on 2011-04-14
El script que me sirvió para mi hp 2133, U10.04, kernel 2.6.32.30, está en este link [http://ubuntuforums.org/showthread.php?p=10678334&posted=1#post10678334](http://ubuntuforums.org/showthread.php?p=10678334&posted=1#post10678334)

---

