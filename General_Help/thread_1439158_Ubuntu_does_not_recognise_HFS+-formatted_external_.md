---
title: "Ubuntu does not recognise HFS+-formatted external drive"
date: 2010-03-25
forum: General Help
---

### Post by RiotNOR on 2010-03-25
Heya.

Just did a fresh install of Ubuntu on my Macbook, and lo and behold, it does not recognise anything through firewire. It lists HFS+ just fine with "sudo fdisk -l", but nothing of my external. 

This thing carries all my media, so it would be nice if it would read the big black box. ;)

Yours,
Carl Riot.

---

### Post by tgalati4 on 2010-03-25
Do you have the firewire module loaded?

Open a terminal:

lsmod | grep 1394

or 

lsmod | grep ieee

Also check dmesg for errors regarding firewire or the disk:

dmesg | more

---

### Post by RiotNOR on 2010-03-25
lsmod | grep 1394 reveals...

ra@apophis:~$ lsmod | grep 1394
ohci1394               27174  1 
ieee1394               81277  2 sbp2,ohci1394

---

### Post by tgalati4 on 2010-03-26
So you have the firewire modules loaded.

Unplug the external drive, then in a terminal:

dmesg | tail

Note the time (in seconds since boot) for the last entry.

Plug the drive in and wait a few seconds.

dmesg | tail -50

Post that.

Also, if this machine is dual boot with Mac OS X, then boot into that and check "Apple", "About this Mac", then check the USB and Firewire details.  Look for errors or power overload conditions.  It's possible that the drive is causing the Firewire port to do safety shutdown due to overpower.  If that is the case, use an external power supply.  Also, try changing the firewire cable.  Sometimes they get stepped on, pinched, etc and fail.

---

