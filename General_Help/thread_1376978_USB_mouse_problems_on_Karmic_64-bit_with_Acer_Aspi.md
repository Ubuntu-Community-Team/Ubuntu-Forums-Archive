---
title: "USB mouse problems on Karmic 64-bit with Acer Aspire 5536"
date: 2010-01-09
forum: General Help
---

### Post by jsheppard on 2010-01-09
Hi all,

Since I upgraded to Karmic a few months ago, I have had problems with my usb mouse function. It has been intermittent but not working most of the time - it maybe works about 15% of the time?

I encountered another thread on USB mouse issues awhile back but failed to locate it again. All I know is that other USB devices (iPod, flash drives) are working fine, and there is power going to the mouse even when it does not work since I see the LED/red light on bottom of mouse.

Other than that, I only know to check for recognized devices using 'lsusb'.

Currently [my mouse is not working and] with the mouse plugged in the result is:

Bus 003 Device 010: ID 1267:0210 Logic3 / SpectraVideo plc 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05ac:1263 Apple, Inc. 
Bus 002 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

With the device not plugged in:

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05ac:1263 Apple, Inc. 
Bus 002 Device 003: ID 0bda:0159 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 04f2:b044 Chicony Electronics Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I'm not sure what "Bus 003 Device 010: ID 1267:0210 Logic3 / SpectraVideo plc" means, but it only appears when I put the mouse into one of my four USB ports.

Also, I'm fairly certain this is a software/OS issue because when I boot the laptop with the gparted CD, I can use my mouse fine. As a disclaimer, there was an issue with water spilled on the keyboard a few months back, but I had Jaunty 64-bit at the time and after the spilling, there were only keyboard but not mouse problems, and keyboard problems were solved after removing and drying out. But since the mouse works fine with gparted boot CD environment, I figure it must be something w/ Karmic.

Any help would be appreciated if anyone has any ideas.

Finally, it might be worth noting that sometimes when I unplug the non-working mouse and plug in to a different USB port, the mouse suddenly works for about 0.5 seconds and then stops working again. But sometimes it doesn't work at all when switching, and seems to not matter to which port I switch to.

Thanks!

John

---

