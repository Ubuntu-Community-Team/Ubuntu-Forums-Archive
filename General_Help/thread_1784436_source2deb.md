---
title: "source2deb?"
date: 2011-06-16
forum: General Help
---

### Post by boblizar on 2011-06-16
rumour says "sudo checkinstall -D" instead of su -c 'make install' spits out a deb that i can share with the community...  if this is so, i would like to start hammering out tons of sources.  i already built xscreensaver latest from source.  ive built a linux from scratch virtual machine and gentoo amongst others.  if i learned how to have sources spit out debs i would totally become re-interested in ubuntu.

only i would become a dev/version nazi and keep friends ubuntu up to date also for security reasons.:popcorn:

checkinstall -D?  t or f :confused:

testing the check install says i dont have it installed!  installed, looks like my "make install" is exploding and needs further backend interweaving, but synaptic makes this totaly retarded easy.  =D

---

### Post by andrewthomas on 2011-06-17
Read the documentation.

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

---

### Post by boblizar on 2011-06-17
yeah 2 seconds of playing with it made it self evident of how the installer functions.  ive been working on building my development environment up.

---

### Post by mcduck on 2011-06-17
Yep, checkinstall works, and you don't even need the "-D" switch, as the default package type is already .deb.

There's one thing to keep in mind, though, the packages buiklt with checkinstall aren't the same as properly built .deb packages, they lack most of the extra information, like the info about required dependencies etc. Because of this they aren't well fit for distribution, you shouldn't share checkinstall-made .deb packages unless it's a simple program without dependencies, or you create a list of the dependencies and share it with the package so people can download and install those dpendencies manually.

---

### Post by boblizar on 2011-06-18
hmmm i see, im interested in installing a real time kernel....  how would i pass the --make menuconfig flag?  id also like to ensure the 64gb mem flags flipped. and cut some junk out of the kernel to make it faster.  thanks in advance

---

### Post by boblizar on 2011-06-26
check install seems to fail at every single deb i attempt to make with it.  vlc 1.1.10 fail...  kernel fail.... some simple audio apps, fail...

make install installs my vlc 1.1.10 perfectly i dont get it??

---

### Post by andrewthomas on 2011-06-29
To build kernel packages you should use fakeroot and make-kpkg
For example, here is part of my build script
```
cp /boot/config-3.0.0 .config
make oldconfig
make menuconfig
fakeroot make-kpkg -j7 --initrd --revision=1 kernel_image kernel_headers 	
make-kpkg clean
```

---

