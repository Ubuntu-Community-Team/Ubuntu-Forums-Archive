---
title: "Actual resolution not shown + Sound broken"
date: 2012-09-23
forum: General Help
---

### Post by Jazzyboy on 2012-09-23
Hi,

Just recently started moving to Ubuntu.

I've had a great time messing with Ubuntu on a liveUSB on the desktop.

However, installing Ubuntu on a PC in the living room has resulted in some major issues.
Using a pretty weak computer, but it's perfectly capable of most tasks.

There are two main issues though.

1. In Displays settings, no resolutions are shown above 1024x768. This TV is a 1080p TV and when plugging my other PC into this TV with Windows XP installed(Plus with the same VGA cable), 1920x1080 worked fine. I've tried a ton of solutions from Google but none have worked. Although I still can't work out xorg.conf.

2. Sound's broken. Worked fine on 1st boot. Now it's broken entirely. I've checked the ALSA settings; everything seems fine. Sound just isn't working. The System Settings -> Sound tests result in nothing and no applications output sound.

---

### Post by Jazzyboy on 2012-09-30
BUMP.

I've tried a bunch of solutions but none have worked. I've also tried a clean reinstall. Still no positive results.

I think I may need to doubt my memory though. I don't think I actually did have sound when I first started up the computer.

---

### Post by hal8000 on 2012-09-30
> **Jazzyboy said:**
> Hi,

Just recently started moving to Ubuntu.

I've had a great time messing with Ubuntu on a liveUSB on the desktop.

However, installing Ubuntu on a PC in the living room has resulted in some major issues.
Using a pretty weak computer, but it's perfectly capable of most tasks.

There are two main issues though.

1. In Displays settings, no resolutions are shown above 1024x768. This TV is a 1080p TV and when plugging my other PC into this TV with Windows XP installed(Plus with the same VGA cable), 1920x1080 worked fine. I've tried a ton of solutions from Google but none have worked. Although I still can't work out xorg.conf.

2. Sound's broken. Worked fine on 1st boot. Now it's broken entirely. I've checked the ALSA settings; everything seems fine. Sound just isn't working. The System Settings -> Sound tests result in nothing and no applications output sound.


You need to define "weak" computer, at least state make and model and make of graphics card. VGA is only 800x600 SVGA 1024x768.
The resolution you quote is HDMI.
The video card must be capable of working at this resolution and therefore must have sufficient video memory.

You are plugging in a different PC which gives you desired resolution but again no hardware details or make model of video card.

Xorg,cong is not used in Ubuntu 12.04, hardware is probed and KMS kernel mode settings are used instead.
Without any more detail, it is difficult to answer, which is probably why nobody tried to answer.

If you dont know your hardware provide output from:

sudo lspci | grep VGA

This will show your graphics card.

---

### Post by Jazzyboy on 2012-10-01
Oh sorry, it should have occured to me to post hardware specs in the first place.

I'm unsure how much RAM the PC has, but I believe it's at least 1GB. Might be 3 or 4 gigabyte. I forgot to check.

But here are the rest of the specs:
Pentium 4 3.2Ghz
Nvidia Geforce 8500 GT 1GB
WD250 (250GB)

I also forgot to check the motherboard. The TV's being used at the moment, so I can't check, but I'm pretty sure that the motherboard is fairly standard and supports most standards, at least the standards of a few years ago.

And as I mentioned, the VGA cable's been used in another PC and worked perfectly fine. It's been used to run at 1920x1080, and I believe also above that, and is at the moment, plugged into this monitor at 1680x1050.

---

