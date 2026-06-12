---
title: "Win4lin"
date: 2004-10-20
forum: General Help
---

### Post by andrew on 2004-10-20
Will ubuntu ever develop a patch or kernel to support win4lin. If not, is there a howto guide on what to do

---

### Post by gpiper on 2004-10-20
I'd be interested in this myself. A pre-built/modified kernel would be best, but I'd also be happy with step-by-step instructions that have been checked to work with Ubuntu kernels.

-ghp

---

### Post by rubinstein on 2004-10-20
I have a working Win4Lin Installation in Ubuntu. This is what I did (beware!! rough translation from german, if it breaks something, it's your own fault)

Ubuntu kernel with win4lin

--------------------------
20041020
adjust all directories as needed

apt-get install kernel-package linux-source-2.6.8.1

at first I wanted to use the kernel-source from kernel.org, but somehow all I get when the new kernel boots is a kernel panic. But with the ubuntu-kernel-source and this procedure it works (at least for me).

for make xconfig:
apt-get install libqt3-dev g++

for make gconfig:
apt-get install libgtk2.0-dev libglade2-dev

cd /usr/src
cp linux-source-2.6.8.1* ~
tar jxvf linux-source-2.6.8.1

download win4lin patches an put it in ~
go into the linux-source-2.6.8.1 directory:
patch -Ep1 &lt; ~/Kernel-Win4Lin3-2.6.8.1.patch
patch -Ep1 &lt; ~/mki-adapter26_1_3_7.patch

cp /boot/config-2.6.8.1* /home/ph/linux/.config #copies the old configuration as a starting point 

sudo make xconfig (or make gconfig) and adjust if you want to (I didn't change anything)
save configuration

sudo make-kpkg clean
sudo make-kpkg --initrd --revision=Custom.6 kernel_image
change custom number as needed

sudo dpkg -i kernel-image-2.6.8.1*

reboot

download netraverse installer and follow the instructions

hope that helps a bit

Naturally it would be easier if there is a default Ubuntu-kernel with win4lin patches included...

rubinstein

---

### Post by andrew on 2004-10-23
I am attempting to follow instructions on patching kernel to work with win4lin here are the following error messages.

andrew@firestar:/usr/src $ cd '/usr/src/linux-source-2.6.8.1'
andrew@firestar:/usr/src/linux-source-2.6.8.1 $ patch -Ep1 &lt; ~/Kernel-Win4Lin3-2.6.8.1.patch
[1] 10930
bash: lt: command not found
bash: /home/andrew/Kernel-Win4Lin3-2.6.8.1.patch: Permission denied
andrew@firestar:/usr/src/linux-source-2.6.8.1 $ cd /home

[1]+  Stopped                 patch -Ep1  (wd: /usr/src/linux-source-2.6.8.1)
(wd now: /home)

---

### Post by rubinstein on 2004-10-23
ups, that should be
patch -Ep1 < ~/Kernel-Win4Lin3-2.6.8.1.patch
patch -Ep1 < ~/mki-adapter26_1_3_7.patch

"<" and not "&lt;" (maybe the wiki software changed it)

For a more comprehensive How To one can also look at the "Debian Kernel 2.6 How To" ([http://www.desktop-linux.net/debkernel.htm](http://www.desktop-linux.net/debkernel.htm)). Not everything may be of interest for a Ubuntu system, and you may have to adapt some things...

rubinstein

---

### Post by gpiper on 2004-11-12
> **rubinstein]ups, that should be
patch -Ep1 < ~/Kernel-Win4Lin3-2.6.8.1.patch
patch -Ep1 < ~/mki-adapter26_1_3_7.patch

"<" and not "&lt said:**
> http://www.desktop-linux.net/debkernel.htm[/url]). Not everything may be of interest for a Ubuntu system, and you may have to adapt some things...

rubinstein
 Ok, I finally bit the bullet & decided to try rubinstein's instructions for compiling a new kernel with the win4lin patches incorporated.

I'm happy to report that, with a few corrected typos and a few minor tweaks due to directory structure differences, I now have a fully win4lin-enabled 2.6.8.1 kernel, built from the Ubuntu sources!

I've gotten win4lin successfully installed, win98 up & running, and my most important windows-requiring app (Logos BibleStudy Library) working nicely. 

And I have run into no problems at all with the existing Ubuntu installation -- Warty seems happy as a pig in slop (pun fully intended!)!

Many thanks to rubinstein for his very helpful instructions!

-ghp

---

### Post by kurisutofaa on 2005-02-12
How does win4lin play games? Is it capable to play even some 3D games? How about midi support. My destination is to use Guitarpro on linux and play some mmorpgs.  :wink:

---

### Post by jakeofnote on 2005-09-28
when using the following command in a root console terminal thingy 
apt-get install kernel-package linux-source-2.6.8.1
i get the following error / result
E: Couldn't find package linux-source-2.6.8.1

must be something wrong with my repositories, can you send me your source.list (email / priv msg - your choice) or just post it here

---

### Post by mdr on 2005-11-14
thanks for that info rubenstein - was able to get my eval working.

---

### Post by ebtech on 2006-04-25
Hi I have installed win4lin and vmware when I try to install windows, it goes thru copying of windows files and when it reaches the end, it says that windows cannot boot off of my harddrive because the cluster size is not supported.  What is that.   I have a SATA harddrive.  I think that is the problem.  is there a way around it so I can install windows??  wife still likes to use windows so I need to have it on as well before I get rid of windows partition entirely.   thanks

---

### Post by Jingo on 2006-04-27
How did you install Win4Lin ?
Did you patch your own kernel, or which kernel did you use?

---

### Post by ebtech on 2006-04-28
I have win4linpro6.0.9 it is the debian file I just clicked on it and it said it installed.  I have dapper beta.  does that help????

---

### Post by Norri on 2006-06-27
Has anyone gotten Win4Lin 9x working under Ubuntu 6.06?

I've tried lots of recompiling and stuff and always end up with kernel panics.

When I eventually got around the Kernel panics, other things went wrong with my display.

A precompiled, Ubuntu-specific kernel would be great.

---

