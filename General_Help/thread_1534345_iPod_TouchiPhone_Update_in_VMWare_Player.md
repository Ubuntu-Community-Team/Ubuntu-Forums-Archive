---
title: "iPod Touch/iPhone Update in VMWare Player"
date: 2010-07-19
forum: General Help
---

### Post by andypi on 2010-07-19
Hi,

I've recently got my iPod Touch syncing to a WinXP VM within VMWare Player (Lucid host). All seems to work fine, except I've not got the latest version of iOS on the iPod Touch (iOS 4). Was just wondering if anyone else with the same setup has successfully done the upgrade? I'm slightly wary that I might brick the iPod, forcing me to do a hard reset/restore on another computer (more hassle than it's worth!).

Thanks.

---

### Post by topes78 on 2011-01-11
Don't do it!!  I foolishly tried, and now mine is stuck on the screen with the usb and the itunes...  Every time I try, I get the error that it can't be updated and get the error code for a hardware issue... The stupid thing was working just fine before, now I think I have to bring it down to an apple store (as I even tried on a windows computer).  I guess the moral of the story is that apple, just like windows, equals garbage!  ](*,)

---

### Post by JorisSpekreijse on 2011-04-30
> **topes78 said:**
> Don't do it!!  I foolishly tried, and now mine is stuck on the screen with the usb and the itunes...  Every time I try, I get the error that it can't be updated and get the error code for a hardware issue... The stupid thing was working just fine before, now I think I have to bring it down to an apple store (as I even tried on a windows computer).  I guess the moral of the story is that apple, just like windows, equals garbage!  ](*,)
*bump*
The problem with virtualisation is that the iPhone gets disconnected for a reboot and the virtual environment should directly reconnect the USB connection. When this does not happen, the update fails.

With VirtualBox you can set up the usb connection to auto-reconnect. That helps.
This is also an advice for all the hardware that heavily relies on a solid connection with USB/comm/lpt. Don't do it virtual do it on a physique host.
Virtualisation is great for software, but not for hardware.

But basically Apple is too dumb to make a cross-platform program. ;)

---

