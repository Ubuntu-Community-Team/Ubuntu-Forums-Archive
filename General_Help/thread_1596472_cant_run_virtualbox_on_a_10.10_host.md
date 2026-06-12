---
title: "cant run virtualbox on a 10.10 host"
date: 2010-10-14
forum: General Help
---

### Post by hoppa123 on 2010-10-14
I have made a fresh install of Ubuntu 10.10 and installed Virtualbox from the repository 
Virtualbox runs ok.

BUT when i enable the nvidia drivers to support my dualscreen setup the xserver crahses with the start of virtualbox and i found out also qemu

this i found in the X log

[ 11360.774]
Backtrace:
[ 11360.774] 0: /usr/bin/X (xorg_backtrace+0x28) [0x4a0fa8]
[ 11360.775] 1: /usr/bin/X (0x400000+0x60fcd) [0x460fcd]
[ 11360.775] 2: /lib/libpthread.so.0 (0x7f0ccf3f0000+0xfb40) [0x7f0ccf3ffb40]
[ 11360.775] 3: /usr/bin/X (0x400000+0xbb22f) [0x4bb22f]
[ 11360.775] 4: /usr/bin/X (0x400000+0x2c2d9) [0x42c2d9]
[ 11360.775] 5: /usr/bin/X (0x400000+0x2184b) [0x42184b]
[ 11360.775] 6: /lib/libc.so.6 (__libc_start_main+0xfe) [0x7f0cce35bd8e]
[ 11360.775] 7: /usr/bin/X (0x400000+0x213d9) [0x4213d9]
[ 11360.775] Segmentation fault at address 0x4
[ 11360.775]
Caught signal 11 (Segmentation fault). Server aborting
[ 11360.775]
Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
[ 11360.775] Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[ 11360.775]


I can reproduce the fault. as i did a new reinstall. and same things happen.

---

### Post by Refalm on 2010-10-14
Can you run Virtualbox with just a single screen configured?

---

### Post by hoppa123 on 2010-10-14
> **Refalm said:**
> Can you run Virtualbox with just a single screen configured?

Yes. it runs fine without the nvidia driver. i am swithcing now with the nvidia driver installed. to a single screen. will reply here the result

---

### Post by iponeverything on 2010-10-14
sounds worthy of launchpad. 

[https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

---

### Post by hoppa123 on 2010-10-14
in one screen setup with nvidia driver installed. no problem.

2 screen setup segfault in the xorg log.

---

### Post by migs73 on 2010-10-14
What version of Vbox are you running. 
There was an update on the 11th which included fixes for the Xorg used in 10.10 ([http://www.virtualbox.org/ticket/7306](http://www.virtualbox.org/ticket/7306)) the latest version of Vbox is 3.2.10.
I think the one in the repos is 3.2.8, so you might want to download the one from Oracles website (plus that version allows USB connectivity amongst other things, that you don't get on the one from the repos)

---

### Post by hoppa123 on 2010-10-14
> **migs73 said:**
> What version of Vbox are you running. 
There was an update on the 11th which included fixes for the Xorg used in 10.10 ([http://www.virtualbox.org/ticket/7306](http://www.virtualbox.org/ticket/7306)) the latest version of Vbox is 3.2.10.
I think the one in the repos is 3.2.8, so you might want to download the one from Oracles website (plus that version allows USB connectivity amongst other things, that you don't get on the one from the repos)


i have download the latest from virtualbox, same issues, the fact it does the same on qemu makes it not  really a virtualbox related thing but rather more a bug in ubuntu or nvidia driver

---

### Post by migs73 on 2010-10-14
> **hoppa123 said:**
> i have download the latest from virtualbox, same issues, the fact it does the same on qemu makes it not  really a virtualbox related thing but rather more a bug in ubuntu or nvidia driver

+1

---

### Post by ChrisBirkett on 2010-10-14
Same problem... Interested to hear if anyone finds a solution, and happy to help investigate or provide more info :)

---

### Post by hoppa123 on 2010-10-14
> **ChrisBirkett said:**
> Same problem... Interested to hear if anyone finds a solution, and happy to help investigate or provide more info :)

Switch to single screen. and you can run virtualbox for now :popcorn:

however. i already filed this as a bug !

---

### Post by ChrisBirkett on 2010-10-14
> **hoppa123 said:**
> Switch to single screen. and you can run virtualbox for now :popcorn:

however. i already filed this as a bug !

Thanks! Can't wait for this to get sorted, I'm really looking to switch to Ubuntu Desktop as a primary OS as it's just so easy to use and well supported (this being a prime example) - but I could never live without Outlook for M$ Exchange support, so I'm really looking forward to being able to run XP within a VirtualBox!

---

### Post by ChrisBirkett on 2010-10-31
Many, many thanks to [hoppa123]("http://ubuntuforums.org/member.php?u=1166987") for this:

#download xorg-core src
sudo apt-get source xserver-xorg-core

cd xorg-server-1.9.0

#apply correction to file
sudo vi Xext/panoramiXprocs.c (and replace pWin with pDst on line 637. then <esc>:mad: to save and quit

#install debuild
apt-get install devscripts

#install required libs as i didn't had them
apt-get install debhelper quilt bison flex xutils-dev  x11proto-bigreqs-dev x11proto-composite-dev x11proto-damage-dev  x11proto-xinerama-dev x11proto-randr-dev x11proto-record-dev  x11proto-render-dev x11proto-resource-dev x11proto-scrnsaver-dev  x11proto-video-dev x11proto-xcmisc-dev x11proto-xf86bigfont-dev  x11proto-xf86dga-dev x11proto-xf86vidmode-dev x11proto-dri2-dev  libxfont-dev libxkbfile-dev libpixman-1-dev libpciaccess-dev  libgcrypt-dev nettle-dev libudev-dev libselinux1-dev  x11proto-xf86dri-dev x11proto-gl-dev libxmuu-dev libxrender-dev  libxi-dev x11proto-dmx-dev libdmx-dev libxpm-dev libxaw7-dev libxmu-dev  libxtst-dev libxres-dev libxv-dev libxinerama-dev automake libtool libxfixes-dev libglib2.0-dev

#build the DEB packages
debuild -us -uc -i

cd ..

#install modified xorg-core
dpkg -i xserver-xorg-core_1.9.0-0ubuntu7_amd64.deb

Works for me!

---

### Post by swapii on 2011-10-08
I am running ubuntu 10.10 & installed virtualbox 4.1. After starting the virtual machine its giving an error to me. The error is-

**"The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing**[B]
[COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."[/B]


I have tried executing **"****[COLOR=#0000ff]/etc/init.d/vboxdrv setup[/COLOR]****"** bt its also nt working..
plz anybody help me!!!!!!   ](*,)

---

### Post by coldraven on 2011-10-09
@swapii
Try going to System>Admin>Users and Groups
Make sure that you have added yourself to the vboxusers group.
Then log-out and log back in. (or re-boot)

---

### Post by swapii on 2011-10-11
@coldraven:
hey thanx 4d suggestion.
I have tried this also but its giving an error as- "Kernel driver not installed ( rc=-1908 ) "?????:confused:

---

