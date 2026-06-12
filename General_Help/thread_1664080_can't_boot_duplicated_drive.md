---
title: "can't boot duplicated drive"
date: 2011-01-10
forum: General Help
---

### Post by ZizzerZuz on 2011-01-10
I am moving a Windows partition from a 250 GB drive to a 40 GB drive.  The original Windows partition was 100GB+ along with a linux partitian on the rest.

I have used gparted to reduce the Windows partition to 38 GB.  That partition is sda1 on that drive.  sda2 and another much smaller partition 2.?gb are untouched.

I have connected another IDE drive via a USB drive attatchment.  That drive shows up as sdb when I boot via the Ubuntu-live CD.  I then open a terminal and run Sudo dd if=/dev/sda1 of=/dev/sdb.  The command completes but the newly created 40 gb drive is not bootable afterwards.  The "old" drive is just fine and boots well.

I can access the files when I boot via the live CD but the drive won't boot.  Simply connecting the "new" drive to the HDD cable and booting just gives a blinking curser in the upper left corner.  I can boot via the live CD and access the files however when I try to install Ubuntu it fails.  I get to the step where I should be able to drag the slider to resize the partition giving Ubuntu 10GB.  A pop up confirming you want to proceed appera, I agree and I get and error "Partitioning failed because the chosen free space may not be used.  There are probably too many (primary) partitions in the partition table."

This is a continuation of this thread:
[http://ubuntuforums.org/showthread.php?t=1661088](http://ubuntuforums.org/showthread.php?t=1661088)

---

### Post by C.S.Cameron on 2011-01-10
The MBR is in root, sda not sda1 so sudo dd if=/dev/sda1 of=/dev/sdb does not copy it.
Try sudo dd if=/dev/sda of=/dev/sdb

or you could try installing grub2 from the Live CD.

---

