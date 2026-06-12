---
title: "Sound doesnt work"
date: 2009-10-25
forum: General Help
---

### Post by Adrenochrom3 on 2009-10-25
ok so a couple days ago i installed some stuff via package manager. and i guess something that i downloaded messed with my sound settings. now i have no sound whatsoever. i uninstalled everything i did install, and i still have no sound... what am i supposed to do??

---

### Post by dv3500ea on 2009-10-25
What did you download?
What desktop/laptop model are you on?
What model is your sound card?
What is the output of ```
sudo cat /etc/modprobe.d/alsa-base.conf
```?

---

### Post by HereInOz on 2009-10-25
Same here, I can't put an actual time on it, as I don't use the sound much, but it was working a couple of days ago, and now nothing.  I can get feedback from the microphone through the speakers, but that is about all.

I am using a Sound Blaster PCI card, but haven't pulled the cover off to check the model, but from memory it is a 4130.

Herewith a copy of the alsa-base.conf file.

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

Hope someone can assist.

---

### Post by Adrenochrom3 on 2009-10-26
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2


i have a dell Studio Laptop 1555. at first my sound didnt work at all, but then i got help with it, and it started working. 
( [http://ubuntuforums.org/showthread.php?t=1278873](http://ubuntuforums.org/showthread.php?t=1278873) check comment #7)

and as far as i know, i removed all the things i installed from the package manager that had anything to do with sound. so idk what else to do. lend me a helping hand. :) thanks

---

### Post by Adrenochrom3 on 2009-10-26
??????????????????????????????????

---

### Post by Adrenochrom3 on 2009-10-26
oh and btw these are the packages i installed. dont ask why i installed them, i was just trying to install maya 2009 onto my computer. and it was being gey so i just went along and tried to find things that might help with the installation of it. but some how i messed something up...

also btw, im running ubuntu 9.04 (x64)

Commit Log for Fri Oct 23 01:44:56 2009


Installed the following packages:
blt (2.4z-4.1)
cfortran (4.4-13)
cmake-gui (2.6.2-1ubuntu1)
gdebi-kde (0.4.9)
gfortran (4:4.3.3-1ubuntu1)
gfortran-4.3 (4.3.3-5ubuntu4)
install-package (0.3.1)
kdebase-runtime (4:4.2.4-0ubuntu1~jaunty2)
kdebase-runtime-bin-kde4 (4:4.2.4-0ubuntu1~jaunty2)
kdelibs-bin (4:4.2.4-0ubuntu1~jaunty2)
kdelibs5 (4:4.2.4-0ubuntu1~jaunty2)
kdepimlibs-data (4:4.2.4-0ubuntu1~jaunty1)
kdepimlibs5 (4:4.2.4-0ubuntu1~jaunty1)
kdesudo (3.4.1-0ubuntu1)
libakonadiprivate1 (1.1.2-0ubuntu1~jaunty1)
libaudio-dev (1.9.1-5)
libboost-program-options1.35.0 (1.35.0-8ubuntu5)
libexpat1-dev (2.0.1-4)
libfontconfig1-dev (2.6.0-1ubuntu12)
libftgl2 (2.1.3~rc5-2)
libgl1-mesa-dev (7.4-0ubuntu3.2)
libglib2.0-dev (2.20.1-0ubuntu2.1)
libglu1-mesa-dev (7.4-0ubuntu3.2)
libglu1-xorg-dev (1:7.4~5ubuntu18)
libice-dev (2:1.0.4-1)
libjs-jquery (1.2.6-2ubuntu1)
libpcre3-dev (7.8-2ubuntu1)
libpcrecpp0 (7.8-2ubuntu1)
libphonon4 (4:4.3.1-0ubuntu3)
libplasma3 (4:4.2.4-0ubuntu1~jaunty2)
libpq-dev (8.3.8-0ubuntu9.04)
libpthread-stubs0 (0.1-2)
libpthread-stubs0-dev (0.1-2)
libqt4-assistant (4.5.0-0ubuntu4.2)
libqt4-dev (4.5.0-0ubuntu4.2)
libqt4-gui (4.5.0-0ubuntu4.2)
libqt4-help (4.5.0-0ubuntu4.2)
libqt4-opengl-dev (4.5.0-0ubuntu4.2)
libqt4-scripttools (4.5.0-0ubuntu4.2)
libqt4-svg (4.5.0-0ubuntu4.2)
libqt4-test (4.5.0-0ubuntu4.2)
libqt4-webkit (4.5.0-0ubuntu4.2)
libqt4-xmlpatterns (4.5.0-0ubuntu4.2)
libroot-dev (5.18.00-2.3ubuntu2)
libroot-minuit5.18 (5.18.00-2.3ubuntu2)
libroot5.18 (5.18.00-2.3ubuntu2)
libsm-dev (2:1.1.0-1)
libsoprano4 (2.2.2+dfsg.1-1ubuntu1)
libsqlite0-dev (2.8.17-4build1)
libvtk5 (5.0.4-1.1ubuntu1)
libvtk5-dev (5.0.4-1.1ubuntu1)
libwxbase2.8-0 (2.8.9.1-0ubuntu6)
libwxgtk2.8-0 (2.8.9.1-0ubuntu6)
libx11-dev (2:1.1.99.2-1ubuntu2)
libxau-dev (1:1.0.4-1)
libxcb1-dev (1.1.93-0ubuntu3.1)
libxcursor-dev (1:1.1.9-1)
libxdmcp-dev (1:1.0.2-3)
libxext-dev (2:1.0.99.1-0ubuntu3)
libxfixes-dev (1:4.0.3-2)
libxft-dev (2.1.13-3ubuntu1)
libxi-dev (2:1.2.0-1ubuntu1.1)
libxinerama-dev (2:1.0.3-2)
libxmu-dev (2:1.0.4-1)
libxmu-headers (2:1.0.4-1)
libxpm-dev (1:3.5.7-1)
libxrandr-dev (2:1.3.0-1build1)
libxrender-dev (1:0.9.4-2)
libxt-dev (1:1.0.5-3ubuntu1)
mayavi (1.5-5)
mayavi2 (3.1.0-1ubuntu2)
mesa-common-dev (7.4-0ubuntu3.2)
phonon (4:4.3.1-0ubuntu3)
phonon-backend-xine (4:4.3.1-0ubuntu3)
python-apptools (3.1.0-1ubuntu1)
python-configobj (4.5.3-1)
python-enthoughtbase (3.0.1-1)
python-envisagecore (3.0.1-1)
python-envisageplugins (3.0.1-1)
python-kde4 (4:4.2.4-0ubuntu1~jaunty1)
python-qt4 (4.4.4-2ubuntu6)
python-qt4-common (4.4.4-2ubuntu6)
python-simpy (1.8-1)
python-simpy-doc (1.8-1)
python-simpy-gui (1.8-1)
python-sip4 (4.7.9-1ubuntu1)
python-tk (2.6.2-0ubuntu1)
python-traits (3.0.3-1build1)
python-traitsbackendwx (3.0.3-1ubuntu1)
python-traitsgui (3.0.3-1)
python-vtk (5.0.4-1.1ubuntu1)
python-wxgtk2.8 (2.8.9.1-0ubuntu6)
python-wxversion (2.8.9.1-0ubuntu6)
qt4-designer (4.5.0-0ubuntu4.2)
qt4-doc-html (4.5.0-0ubuntu4.2)
root-plugin-asimage (5.18.00-2.3ubuntu2)
root-plugin-gl (5.18.00-2.3ubuntu2)
root-plugin-proof (5.18.00-2.3ubuntu2)
root-system-bin (5.18.00-2.3ubuntu2)
root-system-common (5.18.00-2.3ubuntu2)
soprano-daemon (2.2.2+dfsg.1-1ubuntu1)
tcl8.5 (8.5.6-3)
tk8.5 (8.5.6-3)
vim-gnome (2:7.2.079-1ubuntu5)
vim-gui-common (2:7.2.079-1ubuntu5)
vim-runtime (2:7.2.079-1ubuntu5)
x11proto-core-dev (7.0.14-2)
x11proto-fixes-dev (1:4.0-3)
x11proto-input-dev (1.5.0-1ubuntu1)
x11proto-kb-dev (1.0.3-3ubuntu1)
x11proto-randr-dev (1.3.0-1)
x11proto-render-dev (2:0.9.3-2)
x11proto-xext-dev (7.0.4-1)
x11proto-xinerama-dev (1.1.2-5ubuntu1)
xlibmesa-gl-dev (1:7.4~5ubuntu18)
xtrans-dev (1.2.3-1)

---

### Post by holycow131415 on 2009-10-26
if you have other linux-images installed in your grub, try booting to an earlier version to see if the sound works. if so, uninstall the latest image, and reinstall it. This worked for me.

---

### Post by dbyjazz on 2009-10-26
downlaod Gnome Alsa Mixer

---

### Post by Adrenochrom3 on 2009-10-27
yea none of that worked. idk what the heck is wrong... i just want my sound to work and none of the answers i have gotten are useful... :/ what can i dooooooooooooooooo?!?!?!  


like im at the point where im about to reinstall ubuntu, cause im not really getting any help with this. but the thing is there are a few files that i worked really hard to get and i dont want to loose them. i dont want to backup my whole system, just the specific files, or a folder that has all the files i want to backup.... is there a way i can do this? i have read forums about backing up your files, but all the ones i read are talking about backing up your whole system. 

if i can just back up a certain folder with the stuff i want to keep please help me out, im getting stressed out about this no sound crap...

---

### Post by Adrenochrom3 on 2009-10-27
also... i forgot to mention... i did go into the users and groups and changed my privileges so i had all the boxes under my user name checked. idk if that had anything to do with my sound problem but just to let yall know

---

### Post by Adrenochrom3 on 2009-10-27
> **holycow131415 said:**
> if you have other linux-images installed in your grub, try booting to an earlier version to see if the sound works. if so, uninstall the latest image, and reinstall it. This worked for me.

hoooooooooooooooooooooooold up wait a min

i did boot in an earlier version of ubuntu (through grub) and my sound works. my ? is how would i go about " uninstalling and reinstalling the latest version?

---

### Post by Adrenochrom3 on 2009-10-27
yes yes it is confirmed. when i boot, automatically i boot into:

"ubuntu 9.04, kernel 2.6.28-16-generic"

my sound does not work.

and when i restarted and booted into:

"ubuntu 9.04, kernel 2.6.28-15-generic"

my sound did work... 


so moving to my above comment, how do i go about uninstalling and reinstalling > ubuntu 9.04, kernel 2.6.28-16-generic <  

so that i dont have to change to ubuntu 9.04, kernel 2.6.28-15-generic every time i want sound???

---

### Post by holycow131415 on 2009-10-27
go into the packet manager.

search "linux-image"

find the image that is giving you trouble. Mark it for uninstallation, apply, it will go through uninstalling, then restart. you should be booting into the earlier image automatically. so go to the packet manager again, search for linux-image, find what you uninstalled, and mark it for installation. it will install, reboot, all should be fine now.

---

### Post by Adrenochrom3 on 2009-10-27
ok i did that, and it didnt seem to work... i marked it for removal. now im not sure but should i have marked it for complete removal?

---

### Post by holycow131415 on 2009-10-27
> **Adrenochrom3 said:**
> ok i did that, and it didnt seem to work... i marked it for removal. now im not sure but should i have marked it for complete removal?

you mark your most recent version for removal, then click apply to make the changes.

---

### Post by Adrenochrom3 on 2009-10-28
yes yes i did that, unfortunately it did not fix my sound problem for that image... i might as well just remove that image and keep it off, cause it doesnt seem like im going to be able to fix it...

---

