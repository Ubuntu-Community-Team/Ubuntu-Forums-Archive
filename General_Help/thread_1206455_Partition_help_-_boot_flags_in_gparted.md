---
title: "Partition help - boot flags in gparted"
date: 2009-07-07
forum: General Help
---

### Post by zaffod on 2009-07-07
Hi, 
A few weeks ago I was still running gutsy. Recently did a clean install of jaunty like this:

I have two hard disks. One was partition as / and /home. The other was a scratch disk. That was gutsy. 

When I installed jaunty, I opted to install / on the second drive and mounted my old /home as the new /home for juanty. 

All worked well and I now have a stable juanty installation. And gutsy is still there too but I haven't tried to boot it. 

Now I want to recover the space from the old gutsy / partition. 
Gparted shows this old / partition with a boot flag. The partition is not mounted and not used for anything. 

Why is it marked as boot?

The new / partition on the second drive does not have a boot flag. 

Can I safely unmarked boot on the old / partition?
Do I need to mark the new / as boot?

---

### Post by plucky on 2009-07-07
> Can I safely unmarked boot on the old / partition?

If you mark the new / partition using gparted with the "boot" flag,it will remove the "boot" flag off the old partition.

I don't think Linux bothers about the boot flag,as I just tried changing the boot flag using gparted to a different partition and my system booted off the partition that had the boot flag previously.

> Now I want to recover the space from the old gutsy / partition. 

Deleting and resizing partition will change the UUIDs' of the partition and could cause the partition not to mount,as fstab now uses UUIDs' to identify partitions.Be careful with this.A simple edit of the /etc/fstab file will fix any problems.


Good Luck

---

### Post by SteveDee on 2009-07-07
> **zaffod said:**
> Hi, 
A few weeks ago I was still running gutsy. Recently did a clean install of jaunty like this:

I have two hard disks. One was partition as / and /home. The other was a scratch disk. That was gutsy. 

When I installed jaunty, I opted to install / on the second drive and mounted my old /home as the new /home for juanty. 

All worked well and I now have a stable juanty installation. And gutsy is still there too but I haven't tried to boot it. 

Now I want to recover the space from the old gutsy / partition. 
Gparted shows this old / partition with a boot flag. The partition is not mounted and not used for anything. 

Why is it marked as boot?

The new / partition on the second drive does not have a boot flag. 

Can I safely unmarked boot on the old / partition?
Do I need to mark the new / as boot?

When your computer is powered up, BIOS probably selects sda1 as the primary boot drive, which uses the first 512bytes to determine what to do next. It doesn't matter that 9.04 is on another drive, just so long as Grub is initiated and can then load 'buntu from the correctly specified location.

But if you wipe the primary drive (sda1) your system will probably no longer boot. You can check this by going into BIOS and changing the boot drive.

---

### Post by danwood76 on 2009-07-07
> **SteveDee said:**
> But if you wipe the primary drive (sda1) your system will probably no longer boot. You can check this by going into BIOS and changing the boot drive.

Not true as the MBR contains the boot code and not the partition.
The partition is located after the boot block.

Removing boot flags is fine as grub looks for itself on a specific device and boots off that. (defined in /boot/grub/menu.lst)
This is the same way windows works with its bootloader too.

---

### Post by zaffod on 2009-07-13
danwood, you were right on both counts:

The boot flag makes no difference to booting. Linux muxt not use these for booting.  

    and

Formating my original OS partition did not impact booting. So the MBR does not reside on the partition. 

Cheers!

---

