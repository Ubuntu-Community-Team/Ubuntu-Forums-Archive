---
title: "Acer Aspire One wrong resolution"
date: 2011-01-14
forum: General Help
---

### Post by swope on 2011-01-14
My Acer AspireOne netbook has a native resolution of 1024x600.  Most times I start up, the image is 800x480 against the left edge, black bar on the right side, and a repeated image at the bottom. (I can attach a picture if needed.)

I've been seeing this problem since Ubuntu 9.10, but it's more common recently with 10.10.  If I keep shutting down and powering back on, eventually it will come up in 1024x600 as I desire.  If that happens, then I avoid shutting down and only use Suspend instead.  However, anytime I need to reboot (for updates, etc.) the 800x480 comes back.

The Acer logo / BIOS splash screen is also in 800x480, but I only see it switch back to 1024x600 after Ubuntu loads and is shut down. (Repeatedly clicking on/off/on/off never results in the resolution changing to 1024x600.)  So, I'm still suspicious that Ubuntu is causing this (no hardware).  WinXP used to be on this machine, and the problem was never seen.

I don't think any proprietary drivers are needed (but I am still a Ubuntu noob.)  When the problem is occurring, I see this result for xrandr:
```
swope@netbook:~$ xrandr
Screen 0: minimum 320 x 200, current 800 x 480, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 800x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x480        60.0*+
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1
```I've attempted following cvt/newmode/addmode methods I've seen on other posts, but failed:
```
swope@netbook:~$ cvt 1024 600 60
# 1024x600 59.85 Hz (CVT) hsync: 37.35 kHz; pclk: 49.00 MHz
Modeline "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
swope@netbook:~$ xrandr --newmode "1024x600_60.00"   49.00  1024 1072 1168 1312  600 603 613 624 -hsync +vsync
swope@netbook:~$ xrandr --addmode "LVDS1" "1024x600_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26
```I haven't been able to find xorg.conf ... but I've read that recent versions of Ubuntu create the content dynamically.
Not sure what other details I should be including, at the risk of making this post too long.

Any suggestions?

---

### Post by mike555 on 2011-01-15
I have an Acer Aspire One and it works great in several versions ........ perhaps you should reinstall....     (of course backup first.

---

### Post by swope on 2011-01-15
I'd thought the same thing, months ago, when I installed Ubuntu 10.10.  However, the problem has been harder to get around with newer versions. (More shotdowns...)

That is a good reminder to check that my backup process is still working.

---

### Post by drakide on 2011-01-15
If you are not sure if any drivers are required why don't you check it?
(System > Administration > Hardware Drivers)

---

### Post by swope on 2011-01-15
I don't see "Hardware Drivers" but I do see System > Administration > Additional Drivers.  The list is empty and the heading says "No proprietary drivers are in use on this system."

This is the reason I don't think additional drivers are needed.

---

### Post by Gillingham on 2011-01-15
For whats its worth my acer aspire one does have the right resolution.  I don't recall any special steps when I set it up.  

I can confirm that I also see the "No proprietary drivers are in use on this system message" 

When I run xrandr I get```
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 195mm x 113mm
   1024x600       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  
```

David

---

### Post by swope on 2011-01-15
Thanks.  I can see that xrandr output on the odd occasion that my computer boots up in that mode.  So I know the machine and drivers are capable of it, but for some reason the 800x480 is really stubborn.

I'll be looking for a few hours of free time to re-install.  That seems to be the best plan yet.

---

### Post by elisimmer on 2011-03-01
I've been having this issue myself.
I posted about the issue here:
[http://www.techsupportforum.com/forums/f108/acer-aspire-one-boots-with-wrong-resolution-554244.html](http://www.techsupportforum.com/forums/f108/acer-aspire-one-boots-with-wrong-resolution-554244.html)

I wonder if this is an issue with the OS or the Acers themselves.

---

### Post by Brandex07 on 2011-05-08
I had a similar issue with my toshiba l505 laptop and it  was driving me crazy. I finally figured out if you go into monitor  preferences, within ubuntu, the menu will show that there are two  displays in detection. If you click on the "unknown" monitor and click  "off" and fix "laptop" resolution to its highest, save as default and  reboot, the issue seems to go away.

---

