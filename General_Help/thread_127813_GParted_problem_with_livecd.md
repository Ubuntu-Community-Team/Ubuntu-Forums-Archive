---
title: "GParted problem with livecd"
date: 2006-02-09
forum: General Help
---

### Post by gigoguy on 2006-02-09
Hope I'm in the right section of the forums...
Trying to resize my ~240gb ext3 partition from Gparted on the breezy live dvd.  I get a message saying that the device is busy and I should reboot (which doesn't help).  Details: I'm booting with options noapic and nolapic.  The partition is also my primary/boot partition which the non-cd version of breezy currently lives on.  Doesn't make any sense to me - I'm pretty sure that the live dvd doesn't mount my drive.  Anybody able to help a newbie?

From the console, mount shows me:

/dev/mapper/casper-snapshot on / type auto (rw,noatime)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

Thanks much for any help
-gigoguy

---

### Post by WildTangent on 2006-02-10
I had this problem too on a friends computer when I resized the windows partition (to give Ubuntu more room) and reinstalled Ubuntu. I could clear the Ubuntu partition, but was unable to resize the Windows partition. I ended up just using the partitioner on the install CD to do it, choosing to custom make the partitions. I made the size of the partition smaller.

-Wild

---

### Post by gigoguy on 2006-02-12
Problem solved:

Seems that the livecd scans for a swap partition, and if it finds it, uses it.  Need to stop it from doing so with swapoff.  Also, the tiny (32mb) Gparted livecd worked flawlessly.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

