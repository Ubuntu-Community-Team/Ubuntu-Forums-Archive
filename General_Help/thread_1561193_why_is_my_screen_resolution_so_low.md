---
title: "why is my screen resolution so low?"
date: 2010-08-25
forum: General Help
---

### Post by pedrogent on 2010-08-25
hello all:

i just installed 10.04.1 and have done a quick apt-get update/apt-get upgrade.

the problem is i'm running a 1920 x 1080 display using a geforce gtx460, yet the screen is cropped in at 1280 x 1024. i have the option to go lower only.

i first tried to install the nvidia binary in the old-fashioned way of (system > administration > hardware drivers) but this reported that there are no proprietary drivers in use and there was no option to 'switch one on'.

i guess my hardware is too new so i want to install the drivers available at nvidia's website (256.44). this adds support for my gpu.

i tried to install these by exiting x but this just resulted in some sort of system hang. the function keys on my keyboard seem to be 'non-functional' too, making a ctrl+alt+f1 not do what it should. i think this may be a problem with the mac keyboard i'm using.

so... is this just a waiting game? can i get into a virtual console somehow else (perhaps during bootup)? is there a way i can exit x without the system hang? is there another way of installing some workable drivers? should i be altering my xorg.conf?

any help would be greatly appreciated.

:D

---

### Post by micheledm on 2010-08-26
first of all be sure that all of your nvidia related packages are uninstalled (sudo apt-get remove --purge nvidia-*) then stop X (sudo service gdm stop). at this point try again the installation of the official drivers and see what happen.

in order to change the resolution, when nvidia drivers are installed, don't use the ubuntu tool, instead use nvidia-settings

---

### Post by pedrogent on 2010-08-27
cheers i'll try that and report back.

---

### Post by pedrogent on 2010-08-29
> **micheledm said:**
> first of all be sure that all of your nvidia related packages are uninstalled (sudo apt-get remove --purge nvidia-*) then stop X (sudo service gdm stop). at this point try again the installation of the official drivers and see what happen.

the purge went ok. but i get to the same point when i stop gdm. i.e. a strange, non-usable black screen. and then i have to hard reboot.

---

### Post by pedrogent on 2010-08-29
ok so i got this up and running by booting into a recovery session. then,

```
telinit 3
sudo sh NVIDIA*
```

and then followed the prompts.

```
sudo service gdm start
```

and we're good to go. thanks for the help.

pedro.

---

