---
title: "Resolution Disabled and Monitor:Unknown"
date: 2011-05-26
forum: General Help
---

### Post by therimalaya on 2011-05-26
I'm very much new to Ubuntu and any other linux platform. I'm using **Intel ****D845GVFN** Motherboard with graphic card inbuilt in it. My monitor is 14' CRT, but I have RAM of 1.25 GB.
I installed Ubuntu, but in contrast to my expectation, I got my screen resolution 800x600. I was using 1024x728 resolution in windows XP. When I tried to change the resolution through monitor setting, it shows me **Monitor:Unknown**. Further, The **resolution and refresh rate are also disabled**.

Please help me, I like this Ubuntu very much and I'm feeling very good on leaving the windows system, at list i don't have to depend on windows system any more.
:confused:

---

### Post by wildmanne39 on 2011-05-27
> **therimalaya said:**
> I'm very much new to Ubuntu and any other linux platform. I'm using **Intel ****D845GVFN** Motherboard with graphic card inbuilt in it. My monitor is 14' CRT, but I have RAM of 1.25 GB.
I installed Ubuntu, but in contrast to my expectation, I got my screen resolution 800x600. I was using 1024x728 resolution in windows XP. When I tried to change the resolution through monitor setting, it shows me **Monitor:Unknown**. Further, The **resolution and refresh rate are also disabled**.

Please help me, I like this Ubuntu very much and I'm feeling very good on leaving the windows system, at list i don't have to depend on windows system any more.
:confused:
Hi, go to administration click on additional drivers and see if there is a driver for your video card,if install it and reboot.

---

### Post by therimalaya on 2011-05-27
I had already checked there, but it is empty there... I have no option... Someone suggest me to edit xorg.conf but don't know the idea of setting it for my graphic card support. Further, I once tried to copy and pasted the setting from net, but it has created problem and i had to remove those settings.

Someone please help me..

---

### Post by Grenage on 2011-05-27
Can you provide the make and model of your monitor?

Copying random xorg.conf examples from the internet is rarely successful.

---

### Post by therimalaya on 2011-05-27
My Monitor is PHILIPS 105E6 14" CRT

---

### Post by Grenage on 2011-05-27
> **therimalaya said:**
> My Monitor is PHILIPS 105E6 14" CRT

Try this:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```

```
gksu gedit /etc/X11/xorg.conf
```

Add the config below, save, and reboot.

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "Philips"
	ModelName "105E6"
	HorizSync 30 - 54
	VertRefresh 50 - 120
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel D845GVFN"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
EndSection
```

If that does not work, we can add a modeline.  I am going to assume, judging by the monitor specs, that you had 1024x768 at a very low refresh rate?

---

### Post by therimalaya on 2011-05-27
This worked man... You are great,.. I am very very happy.. Thank you very much..
Thank you again

---

### Post by Grenage on 2011-05-27
Always a pleasure.

---

### Post by therimalaya on 2011-07-14
Again I got a problem, I changed my monitor yesterday, It is DELL 20". When i join it, ubuntu though detected the monitor, it is unable to give high resolution. It use 1024 x 768, so that the display of my monitor is stretched. Please help me, all other configuration is same as above in  this thread. I have no idea how to create the conf.org file, please suggest me... for the right configuration.

---

### Post by Grenage on 2011-07-14
No problem; post the full model number of the monitor, and we'll make the appropriate adjustments.  If you'd rather see if normal auto-detection will work, you can try renaming xorg.conf to xorg.conf.old.

---

### Post by therimalaya on 2011-07-14
The Monitor is 20" LED of Dell with model Number IN2020M

---

### Post by therimalaya on 2011-07-14
I copied and paste the above detail to create config.org, i used the model number and vendor name as of the new monitor, but i cannot setup the

HorizSync ??
VertRefresh ??

for 1600x900 resolution...

---

### Post by Grenage on 2011-07-14
I can't find the frequency ranges for that monitor, maybe they are listed in the manuals you have?

Either way, it might not matter *too* much if they are wrong, as long as you have a modeline in there - I'm not sure as I've never done it.  So something like this:

```
Section "Monitor"
	Identifier "Monitor0"
	VendorName "dell"
	ModelName "in2020m"
	HorizSync 30 - 83
	VertRefresh 50 - 75
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel D845GVFN"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1600x900" "1280x1024" "800x600" "640x480"
	EndSubSection
EndSection
```

---

