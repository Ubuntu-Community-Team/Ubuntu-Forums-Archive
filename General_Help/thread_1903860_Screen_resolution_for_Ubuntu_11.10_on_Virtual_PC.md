---
title: "Screen resolution for Ubuntu 11.10 on Virtual PC"
date: 2012-01-03
forum: General Help
---

### Post by eheck on 2012-01-03
I recently tried to upgrade an older installation of Ubuntu (Maverick, when was that?) on Virtual PC to 11.10. The upgrade failed and the system was unusable afterwards. Rather than trying to repair it I decided for a fresh install.
The installer was freezing on the first two tries, but ran successfully after I configured more memory. The system still seems a bit slow. I can live with that, however.
The problem is that I can't change the screen resolution.
Following the steps described at [https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions](https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions), I get:
```
~$ xrandr -q
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 400 x 300, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0
   640x480        60.0
   680x384        60.0
   512x384        60.0
   400x300        60.0     56.0
~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default
~$ xrandr --addmode default 1024x768_60.00
xrandr: Failed to get size of gamma for output default
~$ xrandr --output default --mode 1024x768_60.00
xrandr: Failed to get size of gamma for output default
xrandr: screen cannot be larger than 800x600 (desired size 1024x768)
```

What is the "Failed to get size of gamma" line trying to tell me?
Anything else I can try? The previous version of Ubuntu ran at a higher resolution without any problems.

---

### Post by mcduck on 2012-01-03
Have you installed the guest additions on the Ubuntu? Pretty much every virtualisation software requires you to do that to get the drivers for the virtual hardware.

I have no idea what the package for Virtual PC is called, though. Virtualbox has VboxGuestAdditions, WMware has WMware Tools  and so on. So check the Virtual PC manuals to find out what the additions package is called and how to install it on the guest OS.

---

### Post by eheck on 2012-01-03
Virtual PC doesn't officially support Linux guests, "guest additions" or what they're called are there for Windows only (AFAIK, I will check this again). I have a few older Ubuntu versions running on Virtual PC without problems (they're for software testing only so I don't know if *everything* works, but it's enough for me).

---

### Post by mcduck on 2012-01-03
In that case I'd recommend using VirtualBox instead. The open source edition is free and works perfectly with Linux systems.

---

### Post by eheck on 2012-01-04
I once tried building the VirtualBox OSE on a Mac and it was such a pain that I never bothered with it again. Maybe building on Windows is more straightforward. (The prebuilt versions were not licensed for company use last time I checked).
Thank you anyway.

---

### Post by eheck on 2012-01-04
Just remembered something. I did edit xorg.conf in the Ubuntus that are running fine. I increased the value of HorizSync.
What is the current preferred way to achieve the same?

---

### Post by mcduck on 2012-01-05
> **eheck said:**
> Just remembered something. I did edit xorg.conf in the Ubuntus that are running fine. I increased the value of HorizSync.
What is the current preferred way to achieve the same?

Same as before; even though the xorg.conf file doesn't exist by default, if you create it any options you add there will still be used.

---

