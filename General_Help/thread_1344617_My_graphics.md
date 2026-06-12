---
title: "My graphics"
date: 2009-12-03
forum: General Help
---

### Post by yaqubyahya on 2009-12-03
Hi, i just installed ubuntu and i know the really basic commands and how to use it...I have used ubuntu a couple of times before.(I am a very experienced 13 year old boy.)

I have an nvidia Geforce4 Ti 4200 Graphics card, i installed the proprietery drivers, which fixed the screen but the only probelm is that im only getting resolutions of upto 640x480

when on windows (dual booting) i work at my comfortable resolution which is at 1280x1024

Do you know any way i could get to that resolution?

I hope you can help, i will really appreciate it.
:KS

---

### Post by pedro_orange on 2009-12-03
Try

```
sudo apt-get install nvidia-settings
```

This should add a configuration application to your menu. Hopefully you can reconfigure your x-server there.

---

### Post by yaqubyahya on 2009-12-03
Ah, i have tried using the nvidia settings panel, that shows the exact same resolution modes which i can choose from, 640x480, and there arnt much things in that panel to add a new mode etc.

Is there anyway to maybe override the default resolution its showing? and maybe add 1280x1024?

---

### Post by pedro_orange on 2009-12-03
Okay, have a look and see what your /etc/X11/xorg.conf says. The resolutions available to you might be set in there.

If they are, try renaming xorg.conf and rebooting. This should force x to automatically detect the settings.

---

### Post by Grenage on 2009-12-03
If the above doesn't work, then your machine is probably having issues detecting the screen's capabilities.  If so, please post your monitor's make and model.

While xorg.conf IS redundant in 9.10, detection problems can be resolved using it.

---

### Post by yaqubyahya on 2009-12-03
> **pedro_orange said:**
> Okay, have a look and see what your /etc/X11/xorg.conf says. The resolutions available to you might be set in there.

If they are, try renaming xorg.conf and rebooting. This should force x to automatically detect the settings.

I have checked in the file, in the section "screen"

There are no resolutions set in there.:S

---

### Post by yaqubyahya on 2009-12-03
The make is Asus, and the model number is MM17D.

---

### Post by pedro_orange on 2009-12-03
Okay, so perhaps if you manually specify some resolutions this may help. As the above poster said xorg.conf isn't really used (cause of automatic detection) but it can help.

Google some examples of xorg.conf - resolutions are specified in a subsection.

---

### Post by yaqubyahya on 2009-12-03
I have tried that and it ended up in me reinstalling ubuntu.

I will post my xorg.conf code.

---

### Post by Grenage on 2009-12-03
We'll get you sorted.

The ASUS site gives no real information on their site, so please do the following:

```
sudo apt-get install xresprobe
sudo ddcprobe
```

Post back the "monitorrange" values.

---

### Post by warren181 on 2009-12-03
This might not be the case but when i was testing Ubuntu i could not get the full resolution on the ATI card that i was using. i think some older cards just are not suppoted for higher resolutions.

---

### Post by yaqubyahya on 2009-12-03
```
vbe: VESA 3.0 detected.
oem: NVidia
vendor: NVidia Corporation
product: NV25 Board Chip Rev
memory: 65536kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 80x60 (text)
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
edid: 
edidfail

```This is what it gave me.

What do i do now.?

---

### Post by yaqubyahya on 2009-12-03
Hello? Sorry for spamming, but i really need to fix this :S

---

### Post by Grenage on 2009-12-03
Replace your entire xorg.conf with the code below, then reboot.

```
Section "Monitor"
Identifier "Monitor0"
VendorName "asus"
ModelName "mm17d"
HorizSync 30 - 80
VertRefresh 55 - 75
Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
EndSection

Section "Device"
Identifier "Device0"
Driver "nvidia"
VendorName "4200"
EndSection

Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 16
SubSection "Display"
Depth 24
Modes "1280x1024"
EndSubSection
EndSection
```

> 
Hello? Sorry for spamming, but i really need to fix this :S

Seriously, getting impatient after **_8 minutes_**?

---

### Post by yaqubyahya on 2009-12-03
Ok, Rebooting, Hope this fixes it.

---

### Post by yaqubyahya on 2009-12-03
Lol, I am very impatient when it comes to computers :|

Anyways, Thanks ALOT, it works fine now. you are an Angel!

I love you!(figure of speech):D

---

### Post by Grenage on 2009-12-03
No problem, glad to be of help :)

---

