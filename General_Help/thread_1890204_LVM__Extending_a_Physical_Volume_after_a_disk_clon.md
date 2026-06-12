---
title: "LVM:  Extending a Physical Volume after a disk clone to a larger drive?"
date: 2011-12-03
forum: General Help
---

### Post by UNubTu on 2011-12-03
I am sort of a nub to Linux so please pardon my nubness.

I originally installed Oneiric on a 120GB HDD while I played around with it to see if I liked it.  Now that I decided to keep it, I wanted to move my install to a larger HDD.  I cloned the 120GB to the 750GB using a Live CD (sudo dd if=/dev/sda of=/dev/sdb).  Then shut down the PC, yanked the 120GB and moved the 750GB to the same connections.  Boots up just fine.

However. I originally set up the partitions with a 500MB /boot and the rest in LVM as encrypted, containing my /root, /swap, and /home.

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      976895      487424   83  Linux
/dev/sda2          976896   234440703   116731904   83  Linux

Disk /dev/mapper/sda2_crypt: 119.5 GB, 119532417024 bytes
255 heads, 63 sectors/track, 14532 cylinders, total 233461752 sectors

 --- Physical volume ---
PV Name               /dev/dm-0
VG Name               vg1
PV Size               111.32 GiB / not usable 3.00 MiB

Now I am obviously still using only 120GB of the new 750GB drive.  I'm familiar with extending logical volumes and resizing but I can't figure out how to extend the physical volume.  Is it possible to extend the physical volume to use the additional 630GB of new the drive?  I can't seem to dig up this information any where.

Any guidance would be appreciated!

---

### Post by galvatron408 on 2011-12-03
on your pvdisplay of the volume, what does it say about free PE?

---

### Post by thaelim on 2011-12-03
Very simple: pvresize /dev/sda2

---

### Post by UNubTu on 2011-12-14
I actually ended up wiping and reloading on to the new drive.  I wasn't too far into a new install so it wasn't all that much to wipe it.  It wasn't necessarily the inability to extend the drive that forced me into that route.  The new drive was one of those 4K sector drives and was giving me all sorts of alignment errors when running fdisk and trying to fix those seemed like more of a hassle than just reloading.

Thank you for the input though as I will stash that away for future use!

---

