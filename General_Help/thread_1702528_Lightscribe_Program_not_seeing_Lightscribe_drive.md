---
title: "Lightscribe Program not seeing Lightscribe drive"
date: 2011-03-07
forum: General Help
---

### Post by daldude on 2011-03-07
I have this lightscribe program** ** [SIZE=1]**qlscribe - Qt lisghtScribe **and when I try to print a Lightscribe Label it gives me an error that it can't find any Lightscribe Drives. I had to reinstall the Lightscribe Drivers for some reason after the latests update by typing this command 

sudo dpkg -i --force-architecture lightscribe-1.18.21.1-linux-2.6-intel.deb

I confirmed Lightscribe was installed by typing  

dpkg -s lightscribe

and it returned this message

Package: lightscribe
Status: install ok installed
Maintainer: Hewlett-Packard Company
Architecture: i386
Version: 1.18.21.1
Description: LightScribe System Software
 Copyright: 2005 by Hewlett-Packard Company, All Rights Reserved.
 LightScribe System Software

and still I the program says it can't find my Lightscribe Drive this is the error it gives me

[/SIZE] p, li { white-space: pre-wrap; } Error on request: Launch helper exited with unknown return code 127
p, li { white-space: pre-wrap; } Cannot find any lightScribe drive


I've been having nothing but problems since I had to reinstall Umuntu 10.04-64-bit sometimes when I boot up I loose video and have to do a ctrl alt del to reboot safely and after this latests update I had to mess around with Mobile Media Converter to get it to work again by reinstalling and copying missing files, plus all Youtube videos are in black and white unless I use the Pop Out option.
If I wanted All this aggravation I would just continue to use XP as my main OS.


[SIZE=1]





[/SIZE]

---

### Post by daldude on 2011-03-08
I fixed it (As Of 3/8/2011 12:40 EST) I booted up in Recovery Mode and selected Attempt to fix broken packages and for once this Actually Worked!! Un Believable!!:biggrin:
I can't believe this option actually worked and fixed something that was broken in Ubuntu:):grin:
I figured it was pointless to try but I tried anyway just to say I tried it and actually WORKED!!:guitar:

---

