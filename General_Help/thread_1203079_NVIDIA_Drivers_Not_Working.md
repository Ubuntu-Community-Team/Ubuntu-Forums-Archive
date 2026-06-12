---
title: "NVIDIA Drivers Not Working"
date: 2009-07-02
forum: General Help
---

### Post by HSKR on 2009-07-02
I installed the NVIDIA drivers for my NVIDIA 9800 GT graphics card, using guides that I have used before with similar NVIDIA cards, went through the setup, and rebooted.

I get to the screen about Ubuntu running in low graphics mode, and I configure my screen settings (Dell 1703FP digital) and then go to graphics card, select by model, NVIDIA, and choose GeForce (as there is no GeForce 9 series option), and login.

My monitor is still 800x600, instead of 1024x768, so I go to change it in System > Preferences > Screen Resolution, but my monitor is unknown, and there are only two resolution options, 800x600 and 640x480.

I go into Terminal, and run sudo displayconfig-gtk, and once again, configure my settings, and then log out as it says to do. I then get the low graphics mode window again, reconfigure, and log in. Nothing changes.

Why isn't this working? I've done this on an NVIDIA graphics card before, and it has worked fine. Perhaps Ubuntu 8.04 doesn't support GeForce 9 Series cards?

Graphics Card: NVIDIA GeForce 9800 GT
Ubuntu Version: 8.04

---

### Post by Denis on 2009-07-03
I can't really help. But I have the exact same card and installing the drivers worked very well in Ubuntu 8.10. 

I think I installed the drivers through administration > hardware drivers. 

When you try to install the drivers, is it only a resolution problem you have? Most likely the drivers are not installed or they are not being used. Maybe you can check out /etc/X11/xorg.conf 

You should have something like this: 
```
Section "Device"
    Identifier     "Device0"
    Driver         "**nvidia**"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
EndSection
```

You could try to install the drivers through synaptic (package management) or completely reset X (command: dpkg-reconfigure). 

I hope some of this helps...

---

### Post by HSKR on 2009-07-03
System > Administration > Hardware Drivers says there are no proprietary drivers in use on this system. I looked up my xorg.conf file and reset the devices using:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

So now the graphics card and monitor sections read:

> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by Denis on 2009-07-03
In "Hardware drivers" you should see your graphics card in the list (like in the window below). If you click on activate, the driver should install automatically. 

[IMG]http://users.telenet.be/dionos/screenshot1.jpg[/IMG]

If your card is not in the dialog list, you could try Synaptic to install the driver (look for nvidia-glx). 

Maybe you can point us to the guide that you followed?

---

### Post by UKBB on 2009-07-03
This is what I get when I check hardware drivers. Would switching to the "version 96" help with video playback or should I stick with the recommended driver?

[IMG]http://img.photobucket.com/albums/v211/ukbankerboy/HardwareDrivers.png[/IMG]

---

