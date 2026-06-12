---
title: "Speeding up Ubuntu 11.10?"
date: 2011-11-05
forum: General Help
---

### Post by Isoroth321 on 2011-11-05
[SIZE=2]Hey folks.


So I was wondering what you Ubuntu wizards out there could give me some pointers on how to speed up my Ubuntu to maximum speed and efficiently. 

 I keep my hard drive clean using Bleach Bit (courtesy of Ubuntu Software Center)  and I log in using the Ubuntu Class no effects desktop. That's about all I do.

If you guys have any other ideas that would be great, thanks.  [/SIZE]<3

---

### Post by lakerssuperman on 2011-11-05
You can enable the startup programs by following the directions here.

[http://shuffleos.com/3496/how-to-enable-all-applications-in-startup-applications-ubuntu-11-10/](http://shuffleos.com/3496/how-to-enable-all-applications-in-startup-applications-ubuntu-11-10/)

This may get you a little more speed when your desktop loads.  As for tweaks Ubuntu is pretty snappy, especially if you aren't using the 3D enabled desktop, but you may want to check out Ubuntu Tweak to really customize your system.

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by bluexrider on 2011-11-05
Where do you want the speed? Running apps. Booting, downloading, what?

The other question would be....do you have the hardware to support 11.10?

You didn't mention what your running....hardware, memory, you know those things that make it go fast.

---

### Post by blackbird34 on 2011-11-05
Yeah. +1 to bluexrider.

And this might help, read about Preload, a little daemon for speeding up the system by loading applications in cache or something. All here:

[http://techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/](http://techthrob.com/2009/03/02/drastically-speed-up-your-linux-system-with-preload/)

---

### Post by Isoroth321 on 2011-11-09
[SIZE=2]I don't know my EXACT specs for my hardware, but I know for sure that they're fairly out-dated.

I'm running on a Intel HP that is like 6 or so years old, with about 2gs of ram with a single core processor.  

I can't get the money to get a decent upgrade on this old timey sense I'm just a unemployed 17 year old high school student lol


[/SIZE]

---

### Post by Isoroth321 on 2011-11-09
[SIZE="2"]I'm sorry for the inaccurate description about the hardware, I looked it up on my system settings

Memory - 1002.0 MiB

Processor - Intel® Pentium(R) 4 CPU 3.06GHz 

Graphics - GeForce 6800 GS/AGP/SSE2 

OS Type - 32-bit

Disk Space - 40g (sad I know)

Hope this helps.[/SIZE]

---

### Post by vandorjw on 2011-11-12
With the latest version of Ubuntu 11.10, the one thing that made it feel much snappier was installing "compizconfig-settings-manager", and disabling some of the fancy features that are useless.

Hint, if you ever cannot find something, use:
*apt-cache search "item"*

General:
-Leave as is

Accessibility:
-Disable everything

Desktop:
-Leave as is

Effects
-Only leave "Window decorations" Enabled

Extras
-Disable Everything

Image Loading
-Disable Everything

The other categories I lefts as they were.

Another thing I did, was turn off the notifications that like to hang around for a couple of seconds.

> sudo mv /usr/share/dbus-1/services/org.freedesktop.Notifications.service /usr/share/dbus-1/services/org.freedesktop.Notifications.service.disabled 


All it does is rename a file. To re-enable, rename it back to original.

**EDIT - video drivers:**
Something else I did was disable nvidia proprietary drivers and install nouveau instead.
The proprietary drivers have more features, but also carry much more baggage. Basic 2D and 3D support is fully working for the geForce 6800. The only place you might lose out is if you install wine and try to play games, or plan on watching a lot of flash movies* in that case you would be better off with proprietary drivers.

*I don't think nouveau can decode flash, so it has to be done by CPU. With the newest Nvidia drivers, flash movies can be processed by your video card, leaving your CPU free to do other things.

---

