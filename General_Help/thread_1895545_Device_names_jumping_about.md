---
title: "Device names jumping about"
date: 2011-12-15
forum: General Help
---

### Post by wvo on 2011-12-15
Hi all,

On a fresh install of 10.04 server, I have 6 disks.  One is the root filesystem, the other 5 have been made into a RAID5 filesystem using mdadm.

The names of the disk devices appear to be jumping about - the root filesystem was installed onto /dev/sda2, but on rebooting, it changed to /dev/sdc2.  A further reboot changed it back to /dev/sda2.  The 5 raid-ed disks change to suit and no one seems the worse for wear (although I do get "mdadm monitoring" emails, saying

         A SparesMissing event had been detected on md device /dev/md0.

I know that /etc/fstab sets mounting according to the disk's UUID, rather than device name.  I am assuming that, as the disks power up at boot, it's first-come, first-served as to device assignments, e.g. /dev/sda2?  That's the only explanation I can come up with, anyway.

Is this normal behaviour?  Is there anything I can do to make permanent device name assignments, rather than having them flap around?

Cheers,
Lyn

---

### Post by dandnsmith on 2011-12-15
Only way I can see is to have all the HDDs spun up and ready before the boot process starts. I know this goes against the grain, where all the emphasis is on trying for a fast boot time. You could get the BIOS involved in fuller checks, if you've curtailed those, but I'm not sure what else would work.
What types of HDD connection are we talking here, as that might suggest something - IDE, SATA, SCSI?

---

### Post by wvo on 2011-12-15
Thanks for the reply, Derek.  They're SATA drives.

---

### Post by dandnsmith on 2011-12-15
Now I'm out of my comfort zone, having all my experience in the last few years in IDE drives.
I'm aware that SATA drives can have oddities, depending on the motherboard/BIOS, but I don't know what to look for. I believe some boards are more 'organised' as to order than others.

---

