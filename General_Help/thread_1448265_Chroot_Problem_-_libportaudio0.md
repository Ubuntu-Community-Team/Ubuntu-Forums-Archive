---
title: "Chroot Problem - libportaudio0"
date: 2010-04-06
forum: General Help
---

### Post by djmashedman on 2010-04-06
Ok so I want to install Guitar Pro 6 for ubuntu. Unfortunately it only supports 32bit karmic and above, I am running 64bit karmic.

So I looked here - 
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
and then decided to chroot and install GP6 in that.
I followed this guide - 
[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)

and everything seems to have worked perfectly with a 32bit karmic.

So when I try to install GP6 I get the following error

```
dpkg: dependency problems prevent configuration of guitarpro6:
 guitarpro6 depends on libportaudio0; however:
  Package libportaudio0 is not installed.
dpkg: error processing guitarpro6 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 guitarpro6

```

So I try to install libportaudio0 using apt-get and it cannot find it (despite the fact that I can find it perfectly fine in my 64bit karmic synaptic.
I also downloaded the .deb file of it, move it to the 32bit karmic and attempt an install but it says

```

(karmic_i386)root@matthew-laptop:/home/matthew# sudo dpkg -i libportaudio0_18.1-7.1_i386.deb
dpkg: error processing libportaudio0_18.1-7.1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libportaudio0_18.1-7.1_i386.deb

```

I'm just wondering how I should get around this?
Any help will be much appreciated!
Thanks. :)

---

### Post by sisco311 on 2010-04-06
libportaudio0 is in the univers repository.

If software-properties-gtk is installed, then run:
```
sudo software-properties-gtk -e universe
sudo apt-get update
sudo apt-get install libportaudio0
```

If not, then edit the sources.list file manually:
[uhelp]community/Repositories/CommandLine[/uhelp]

---

### Post by djmashedman on 2010-04-06
Thanks, that seems to have done the trick. 
:)

---

