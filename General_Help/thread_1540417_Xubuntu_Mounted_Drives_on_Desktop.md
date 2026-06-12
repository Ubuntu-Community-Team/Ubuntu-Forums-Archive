---
title: "Xubuntu Mounted Drives on Desktop"
date: 2010-07-27
forum: General Help
---

### Post by Finalfantasykid on 2010-07-27
I have installed Xubuntu on an old laptop which has a floppy disk.

On the desktop where mounted drives will normally appear, it constantly shows the floppy disk on the desktop even though there is not floppy inside, so I have disabled the desktop from showing mounted drives, however now anything else like a CD or USB drive will not show up on the desktop.  Is there a way to choose what types of devices are shown on the desktop?

I have considered disabling the floppy from the BIOS(assuming that is possible), but I would rather not go down that road just yet.

---

### Post by arrrghhh on 2010-07-27
How did you diasble the desktop from showing all mounted drives?  I'd start with undoing that :D

Next step would probably be to have a look at your /etc/fstab... do you see any entries that don't make sense or look related to the floppy?  Comment 'em out & reboot.

Paste your fstab in code brackets if you're unsure of some entries.

---

### Post by Finalfantasykid on 2010-07-27
Thanks for the suggestion, but in fstab there was no metion of the floppy drive.  All that was there was the linux partition, and the swap.

And actually looking at it again the floppy drive isn't even mounted, when I right click it, I am given the option to mount it, so it is showing up without being even mounted.

---

### Post by arrrghhh on 2010-07-27
> **Finalfantasykid said:**
> Thanks for the suggestion, but in fstab there was no metion of the floppy drive.  All that was there was the linux partition, and the swap.

And actually looking at it again the floppy drive isn't even mounted, when I right click it, I am given the option to mount it, so it is showing up without being even mounted.

Ok then, I have to know... what happens when you mount it!?

---

### Post by Finalfantasykid on 2010-07-28
I get an error if there is no floppy inside.  If there is a floppy, it behaves as you would expect.

---

### Post by arrrghhh on 2010-07-30
> **Finalfantasykid said:**
> I get an error if there is no floppy inside.  If there is a floppy, it behaves as you would expect.

Based on [this](http://ubuntuforums.org/showthread.php?t=591420) thread, commenting it out in fstab should do the trick...

Can you post your fstab if you're unsure of which line to comment out?

---

### Post by Finalfantasykid on 2010-07-30
> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=a81d22bc-5cc5-4cc4-ba3f-e17f3cbd318a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d1f2374d-5cf4-4c55-ae6b-d7cd0e9bbe82 none            swap    sw              0       0


I don't see anything on there that would be the floppy...

---

