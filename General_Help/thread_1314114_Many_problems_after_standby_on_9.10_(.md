---
title: "Many problems after standby on 9.10 :("
date: 2009-11-04
forum: General Help
---

### Post by mjcritchie on 2009-11-04
I've had a quick scout around the forums and it looks like there are loads of people having different issues with Karmic Koala, so I know it's a long shot but I thought I'd throw this in the pot because I can't seem to figure out what's wrong.

I installed Ubuntu 9.10 the other day and it, pretty much, works great once it's booted up. However after my laptop has woken up from standby all kinds of bad things happen:

My wireless network connection disappears. First of all it gets disabled, but then can't find any wireless networks once I enable it again.

Shutdown/restart etc. don't work, neither do many other system related menus, for example System Monitor. I click on the relevant icons in the menu but nothing happens.

If I previously had a Firefox window open, that just greys out and needs to be forced to quit.

That's it so far. It seems like everything breaks after my laptop has been on standby!!

In older versions of Ubuntu I had issues with there being no wireless network after standby, the solution was to open up:

$ sudo gedit /usr/lib/pm-utils/sleep.d/55NetworkManager

then add:

sudo rmmod rt2500pci && sudo modprobe rt2500pci
sudo iwconfig wlan0 rate 54Mb/s

between:

thaw|resume)

and:
;;

But that doesn't seem to work anymore.

Of course I can live without standby, but if anyone can shed any light on what might be causing this problem, I'd be really grateful. 

I'm running an Averatec 1020, with a 1.00GHz Celeron M and 512MB of RAM.

Thanks.

---

### Post by djkrisx on 2010-01-13
same problem but in my case a simple restart fixes everyting

---

