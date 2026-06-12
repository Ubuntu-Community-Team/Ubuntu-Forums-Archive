---
title: "Can't set resolution in AMD Catalyst Control Centre"
date: 2012-02-28
forum: General Help
---

### Post by x1a4 on 2012-02-28
Hi,

On a laptop with a second display connected using HDMI, AMDCCCLE keeps crashing (exit 139) when I try to set resolution on either display.  Other settings are okay.  This happens when I run the Control Centre using su or gksudo.  When I try to run it using the AMD way: "amdxdg-su -c amdcccle", it crashes (exit 3) with the following error: "no graphical method available for invoking 'amdcccle' as 'root'"

There is a bug report about this [here]("http://ati.cchtml.com/show_bug.cgi?id=367") but there is no fix.

The video card is AMD Radeon HD 6300
Driver version 11.8 
CCC version 2.13
Xubuntu version 11.10 (Oneiric)


Anyone know of a solution to this?  I can't configure my displays correctly without this.  

Thank you.

---

### Post by Mark Phelps on 2012-02-29
Is there some particular reason you're using CCC?

I used to use that all the time, then I switched to using the default open-source Radeon drivers, and since I do not need hardware 3D acceleration (don't do gaming), I find I get all the features I need (multiple monitors, multiple desktops, different resolutions) with the open-source drivers and NONE of the hassles trying to get CCC to do what I want.

---

### Post by x1a4 on 2012-02-29
> **Mark Phelps said:**
> Is there some particular reason you're using CCC?

I'm using CCC and AMD's driver because I want 2D acceleration and 3D support.  

Also, I had the open source driver before and it didn't work correctly whenever I plugged-in the second monitor.  I was unable to set resolution on the second display to its native resolution of 1920x1080.  The highest I could set was 1600x900 with black bars on all sides.  The first display (the laptop one) went off the screen prohibiting me from seeing part of the right side. There was also a problem with the wallpaper.  The wallpaper on the first display would appear on top of the wallpaper on the second display.   

I'm hoping that CCC will fix these issues, once I can figure out a way to save settings without crashing.

---

### Post by x1a4 on 2012-03-03
bump :(

---

### Post by yopensource on 2012-03-06
I have this problem too. So I have to remove the driver and use the default driver.
You can setup dual mornitor resolutions by using "Setting Editor".

---

### Post by Grenage on 2012-03-06
Hi, x1a4.

Have you tried using xrandr to set the resolution, as a work-around?  The Arch Wiki is probably one of the best sources of info on this:

[https://wiki.archlinux.org/index.php/Xrandr](https://wiki.archlinux.org/index.php/Xrandr)

If you get stuck, post back!

---

### Post by x1a4 on 2012-03-09
Thanks Grenage.  I'll do it this Saturday and we'll see if I can get things to work right.

---

