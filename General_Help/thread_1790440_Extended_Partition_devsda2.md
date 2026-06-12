---
title: "Extended Partition /dev/sda2"
date: 2011-06-25
forum: General Help
---

### Post by DRSorensen on 2011-06-25
I've recently installed Ubuntu 11.04 onto my hard drive (with Vista) after using the Wubi installer for a month or so. I gave Ubuntu a minimally size partition that I would resize later, but I'm having troubles doing that.

[IMG]http://postimage.org/image/6p97ydtw/[/IMG][IMG]http://postimage.org/image/6p97ydtw/[/IMG][IMG]http://www.freeimagehosting.net/uploads/c8a062de57.png[/IMG]

This is what I get in gparted. It won't let me resize it, I assume, because of the extended partition /dev/sda2. I've tried this in both gparted and Easeus (in Vista). 

Is there any way to resize the /dev/sda5 partition using the unallocated space I already have?

---

### Post by Quackers on 2011-06-25
You can't do it from a mounted system.
Boot from the live cd again (I know you've got one of those :-) ) and open gparted from there. That way the partitions aren't mounted.
Right-click on the swap partition and select "swapoff", first.
Then extend the extended partition to the left. Click on the green tick in the toolbar to apply the change.
Then resize your Ubuntu partition to the left and click on the green tick again to apply the change. Moving a bootable partition does carry a small risk and gparted will tell you that. Click OK to continue.
This step may take a couple of hours, so beware.
When it's finished reboot and hope it's still ok :-)
It has been for me, many times.

---

### Post by DRSorensen on 2011-06-25
Thank you again, Quackers.

---

### Post by Quackers on 2011-06-25
You're welcome :-)

---

