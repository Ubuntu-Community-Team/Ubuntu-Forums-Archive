---
title: "Abt backup and format between 32 and 64 bits"
date: 2009-12-16
forum: General Help
---

### Post by Elie-M on 2009-12-16
hey the thing is my laptop can support the 64bits version of ubuntu but I have the 32 bits installed.

what I need to know is if I backup the 32bits version, format to 64bits and then deploy the image on the 64 bits will the system work fully as 64bits with the programs working correctly as left and installed with full paths and configurations working? or will that do a problem to me?

I'm going from the idea that 64bits is fully backward compatible with 32bits version. (that's what I know If I'm not mistaken :P)

IF YES I CAN, what is the way/software I need to backup my laptop and what's important to know before starting with the whole thing?

and thx in advance :)

---

### Post by philinux on 2009-12-16
To install 64 bit you need to do just that. The 32 bit packages will run on 64 bit but that would defeat the object. The only thing worth backing up is stuff from /home.

I have home on it's own partition so reinstalling is easy.

You dont format to 64 bit. You format the filesystem to ext3 or ext4 which is the default on karmic.

---

### Post by Elie-M on 2009-12-16
I'm not sure that helped me out... I need some more replies plz

---

### Post by ajgreeny on 2009-12-16
What you have is a 32bit filesystem, installed from a 32 bit iso file.  If you want to run the 64 bit version you will need to download the 64 bit iso file from ubuntu and reinstall.  You can not just "upgrade" as you seem to think, nor can you format the partitions as 32 or 64 bit using the installer or gparted; that's not the way it works.

If you are happy with the 32 bit system on your 64 bit hardware, stick with it for now at least.  When ubuntu 10.04 comes out, then perhaps try the 64 bit version, but "if it ain't broke, don't fix it!" is my motto.

---

### Post by Elie-M on 2009-12-17
nah it's not upgrading. I will just reinstalling again. my question is just if I can deploy a 32bits image backup on a 64 bits system and if it works completely or not..

---

### Post by plucky on 2009-12-17
> **Elie-M said:**
> nah it's not upgrading. I will just reinstalling again. my question is just if I can deploy a 32bits image backup on a 64 bits system and if it works completely or not..

If you do a 32-bit image backup of your whole system and then restore it,it will still be running the 32-bit system.

If you backup your files in your home partition and then clean install the 64-bit system and restore your files to the home partition,you will then be running the 64-bit system.

Good Luck

---

### Post by Elie-M on 2009-12-17
> **plucky said:**
> If you do a 32-bit image backup of your whole system and then restore it,it will still be running the 32-bit system.

If you backup your files in your home partition and then clean install the 64-bit system and restore your files to the home partition,you will then be running the 64-bit system.

Good Luck

I'm relatively new to ubuntu.. much like 1 month using it. so just to be sure about it, when u say in ur home partition u would mean everything inside /home/?

AND, doing that will avoid me reconfiguring my system and reinstalling all applications again? (cz seriously, reinstalling again with 700 MB worth of downloads for the applications and updates and libraries is nothing fun... not even close to it :-|:-|)

---

### Post by plucky on 2009-12-18
> AND, doing that will avoid me reconfiguring my system and reinstalling all applications again? (cz seriously, reinstalling again with 700 MB worth of downloads for the applications and updates and libraries is nothing fun... not even close to it 

Your /home contains the configuration files for all the programs that you use and install.Any other software you have installed separately will have to be re-installed.

You are changing from 32 bit to 64 bit!!!.

Why are you changing from 32 bit to 64 bit if you don't want the hassle?

Probably only worth it if you need to run 64bit applications.

Good Luck

---

