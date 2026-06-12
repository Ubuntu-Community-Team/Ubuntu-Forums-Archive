---
title: "NVIDIA Resolution Issue"
date: 2009-11-03
forum: General Help
---

### Post by Felda on 2009-11-03
My NVIDIA settings keep on reseting every time I login or restart my computer. When I do login it says that the resolution and refresh rate are not supported and I have to hook up my computer to a Television first.  Then plug-in the monitor and change the settings to the monitor.  I have run the NVIDIA X Server in administrative mode to save the config file, but after I logout it is like it doesn't save it :evil: I am using Ubuntu 9.04 Jaunty Jackalope, have an NVIDIA GeForce 7300 LE, Dell E196FP LCD screen, and the NVIDIA Accelerated 180 Graphics Drivers.  Any help is greatly appreciated.

---

### Post by tripleaces on 2009-11-04
after you save the config file in the nvidia settings have you tried manually checking the x11 conf file and making sure everything is setup correctly?

I saw a post somewhere similar to this a few days ago that had a solution, I'll try to find it and post re-post the link.

---

### Post by P4man on 2009-11-04
> **Felda said:**
> My NVIDIA settings keep on reseting every time I login or restart my computer. When I do login it says that the resolution and refresh rate are not supported and I have to hook up my computer to a Television first.  Then plug-in the monitor and change the settings to the monitor.  I have run the NVIDIA X Server in administrative mode to save the config file, but after I logout it is like it doesn't save it :evil: I am using Ubuntu 9.04 Jaunty Jackalope, have an NVIDIA GeForce 7300 LE, Dell E196FP LCD screen, and the NVIDIA Accelerated 180 Graphics Drivers.  Any help is greatly appreciated.

run 

```
gksudo nvidia-settings
```

Then you can save the changes to X configuration file

---

### Post by Felda on 2009-11-04
> **P4man said:**
> run 

```
gksudo nvidia-settings
```Then you can save the changes to X configuration file

i have already done this many times before

> **tripleaces said:**
> after you save the config file in the nvidia settings have you tried manually checking the x11 conf file and making sure everything is setup correctly?

i just saved it and then check the config file and everything that I saved is in there

---

### Post by P4man on 2009-11-04
> **Felda said:**
> i have already done this many times before



i just saved it and then check the config file and everything that I saved is in there

are you sure its not making duplicate entries?
Uncheck the "merge with existing file"w hen saving to xorg.conf 
Also try deleting ~/.config/monitors.xml

If that doesnt help, post the contents of your xorg.conf as well as the output of

```
xrandr
```

---

### Post by mbzn on 2009-11-04
Had a similar problem, and deleting the monitors.xml file did the trick for me hope it does the same for you. 

BTW THANX P4man

---

### Post by Felda on 2009-11-04
deleting the monitor.xml file work!  although now I have a weird problem where every time is login or reboot a firefox session opens up right when I login even though I never clicked on the icon or set it to open when I login in startup thing.

---

### Post by DWL52 on 2009-11-04
Hello all. First of all, let me say I'm pretty new to Linux. I also have an Nvidia problem, and maybe someone can help. I'm running Ubuntu 9.04 and have a Nvidia GeForce 5200 card. What I'm trying to do is get the resolution set to 1280x1024 or at least 1024x768. I had it that way before, but don't know how I did it. If I activate the Nvidia Driver in System>Administration>Hardware Devices and reboot, the highest resolution  I can get is 600x400. If I disable the driver and reboot, the highest resolution available is 800x600. I've deleted the /etc/X11/xorg.conf file, I've modified it per everyone's suggestions, but so far nothing works. Any and all help is greatly appreciated.

---

### Post by P4man on 2009-11-05
DWL can you post your system specs (incl monitor), the contents of /etc/X11/xorg.conf and the output of xrandr ?

BTW, are you sure you are configuring your resolution with the right tool?  If you installed nvidia drivers you should use system > adminstration > nvidia X server settings.

---

### Post by DWL52 on 2009-11-05
> **P4man said:**
> DWL can you post your system specs (incl monitor), the contents of /etc/X11/xorg.conf and the output of xrandr ?

BTW, are you sure you are configuring your resolution with the right tool?  If you installed nvidia drivers you should use system > adminstration > nvidia X server settings.

**The system specs are:**
2.8 gig Celeron processor, 2 gig ddr ram, Ubuntu 9.04 on a 500 gig hard drive. The video card is a Nvidia GeForce FX 5200, the monitor is a Spectre model X9W. Yes, I know the monitor is a non plug and play, but the price was right, and I've had the resolution up before, but don't remember how I did it. 

**The contents of /etc/X11/xorg.conf are: (The part you're interested in)**

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

**The output of xrandr is:**

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
   400x300        60.0     56.0  
   320x240        60.0

---

