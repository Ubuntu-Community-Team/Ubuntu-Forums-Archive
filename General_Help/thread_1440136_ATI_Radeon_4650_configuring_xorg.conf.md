---
title: "ATI Radeon 4650 configuring xorg.conf"
date: 2010-03-27
forum: General Help
---

### Post by alex4c on 2010-03-27
I first installed fglrx driver, but some features in Ubuntu 9.10 64bit didn't work right (like recording desktop). So I decided to install radeonHD drivers.
I did this: [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD) , and this: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I changed my xorg.conf file (and I think this is the problem) so it looks like this now:

> Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    ...    
        Driver   "radeonhd"
        Option   "DRI" "on"  
        Option   "AccelMethod" "EXA" 
EndSection
I only change section "Device". 

There's an error that pops up before log in and I have to run Ubuntu in low graphic mode. Here is the error:
> Problem parsing the config file
Error parsing the config file
What should I do?

---

### Post by Mark Phelps on 2010-03-27
Have you tried just removing (or renaming) your Xorg.conf file and rebooting? Since 9.10 no longer relies on that file, you should be able to reboot without it and the open source drivers should then work OK.

IF you want lots of customizing info for ATI cards, the best place to go is the Phoronix forums.  They do LOTS of tweaking with the cards and the drivers.

---

### Post by alex4c on 2010-04-01
Thanks, I'm going to check that forum. 
 I reinstalled Ubuntu so now everything works almost alright. I don't have effects, but recording desktop works perfect. Will I be able to have effects with open-source radeonhd drivers?

My card is in group 2 according to this: **_[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)_**  
I would like to install recent kernel so I can enable 3D acceleration. My current one is 2.6.31.20. 

The question is, how do I install latest stable kernel (which supports  3D acceleration for my card)?[SIZE=2]
[/SIZE] [SIZE=1]I'm using Ubuntu 9.10 64 bit. [/SIZE]

---

