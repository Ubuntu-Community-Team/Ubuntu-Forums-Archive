---
title: "broken apt-get aptitude and dpkg"
date: 2011-12-31
forum: General Help
---

### Post by hogman500 on 2011-12-31
I have been messing g around with Linux on my tablet I had it working fine until I had to restore my tablet and I had to reinstall the startup script what I think happened was that the installer Linux installer replaced my /etc/apt/sources.list file with a debian one and when I tried to install gnash it tried to reinstall does system Packard and messed up all my package management programs. 

It will not apt-get update 

I already fixed my sources.list but it will not update the apt-cache it says 

E:method http has died unexpectedly! 

Dpkg won't install any packages because it says libudev0 is an empty package 

Selecting previously deselected package multiarch-support.
(Reading database ... dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `libudev0': Input/output error
root@Galoula-ARMEL:/#

I think if i install libudev0 it will fix it but I am not sure how to do this without dpkg also I can only work with the command line because I only have basic tools on the GUI half of the system and I have the packages I need I think but have no way of installing them and it is sensor based system. 

Thank you in advance for your help

---

