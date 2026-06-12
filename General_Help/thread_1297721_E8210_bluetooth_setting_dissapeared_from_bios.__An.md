---
title: "E8210 bluetooth setting dissapeared from bios.  Any ideas?"
date: 2009-10-22
forum: General Help
---

### Post by gillza on 2009-10-22
Hi everyone,

Thank you in advance to all who will try to help me with my issue. Firstly, I have spent considerable time searching for a similar issue just googling and going to forums like this one without much luck.

The problem:

A while ago I have purchased a custom built Fujitsu E8210 from fujitsu site. Upon arrival it came with preinstalled windows and whole bunch of software. I was using it as is for a while and then decided to turn off several things from bios in order to increase the battery life and get rid of the devices I did not use. So I disabled COM and LPT ports, as well as turning off IR port and Trusted platform module. Shortly after that I installed my own winodows xp without all the additional software that came with the computer (except for the necessary ones). Later I disabled Bluetooth as well since I did not use it.
A couple of days ago I reinstalled my windows xp and flashed new version of bios from Fujitsu's support site (v1.23) (used my personal configuration number to get the update) and decided to turn on Bluetooth.
I went to bios and the setting for it have disappeared from "Internal Device Configurations". There is not a trace of it. As if it never existed.
I tried downgrading the Bios, but system would not allow it due to a newer version present. I am linking the problem to the bios update but am not sure. I have not checked the bios settings for over a year or so prior to that. Could it have disappeared during that time, i dunno.

In any case, I was wondering if anybody had a similar problem.

P.S. -- Bios is phoenix.

P.S.S. -- I have tried to reinstall the drivers from Bluetooth drivers cd the laptop came with and from Fujitsu support site. Windows does not see Bluetooth module, thus installing drivers will not help and produces an error message saying "Bluetooth module is not detected"

P.S.S.S. -- The laptop came with the recovery dvd which has an image of windows that computer came with and it also flashes bios to v1.20 or so. I am considering as a last resort doing the recovery hoping that it will reflash the bios but I suspect it will not for the same reason as above and also I dual boot the computer with Ubuntu and would like to avoid dealing with the mess with MBR and etc later.

---

### Post by PrePenguin on 2009-10-22
Definately the bios update is the culprit.. There is a jumper on the motherboard you have to set to unprotect the bios to downgrade.

---

### Post by gillza on 2009-10-22
> **PrePenguin said:**
> Definately the bios update is the culprit.. There is a jumper on the motherboard you have to set to unprotect the bios to downgrade.


Thank you. I am a bit hesitant about messing with laptops internals. I have built several desktops, but laptop is different. I hope this is not the only way out of this situation.

---

### Post by PrePenguin on 2009-10-22
> **gillza said:**
> Thank you. I am a bit hesitant about messing with laptops internals. I have built several desktops, but laptop is different. I hope this is not the only way out of this situation.
 
 
 
Might check and see if any supervisor Passwords or to that effect are enabled in the bios that maybe you can manipulate. The jumper setting i was refering to was on a Desktop I am not sure if its the same on a laptop however it would be something to that effect I am betting.. Good luck with it.

---

### Post by gillza on 2009-10-22
All the security settings have been disabled in bios. I have checked, there are no supervisor passwords or similar features enabled. And even though it is pointless in this situation I have tried loading the default settings.

P.S. Thank you to whomever moved my thread, I wasn't sure where it belongs since it is not exactly about Ubuntu :)

---

