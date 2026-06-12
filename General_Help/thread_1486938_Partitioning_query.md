---
title: "Partitioning query"
date: 2010-05-18
forum: General Help
---

### Post by bigseb on 2010-05-18
Atached is a screenshot of my harddrive in Gparted. I need to create a 30Gb partition for XP. How do I do this?

[ATTACH]157395[/ATTACH]

---

### Post by Chesamo on 2010-05-18
Right-click on /dev/sda1 and click "Resize". Make the "Free space following" value "30720". Click "OK".

Right-click in the free space, click "New". Make the partition type "primary". Make the partition NTFS. Click "OK".

Click "Apply".

If you want to dual-boot, I'd recommend installing Windows *first*, then installing Ubuntu. See this guide: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by bigseb on 2010-05-18
Thanks, but when I right-click /dev/sda1 'resize' is blanked...

Help!

---

### Post by Rubi1200 on 2010-05-18
When you right-click on the partition, first select Unmount; GParted will refresh the information and then right-click and choose Resize.

> If you want to dual-boot, I'd recommend installing Windows *first*, then installing Ubuntu. See this guide: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Good luck!

(You may have to Unmount the Swap partition as well)

---

### Post by bigseb on 2010-05-18
Thanks I will try that now now. Another question: Is it possible to set it up in such a way that the XP partition is at the right hand side? I don't know if that would mke a difference to performance...

---

### Post by bigseb on 2010-05-18
UPDATE:

None of those methods you guys mentioned work :(

---

### Post by srs5694 on 2010-05-18
You can only resize a partition that's not in use. Since your single Linux is necessarily in use whenever you boot Linux, you can't resize it from your installed Linux system. Instead, you must use an Ubuntu live CD or some other emergency disc, such as [PartedMagic](http://partedmagic.com) or [System Rescue CD.](http://www.sysresccd.org)

It's certainly possible to put your Windows partition to the right of the Linux partition. In fact, shrinking the Linux partition from the right is likely to be quicker and safer than shrinking it from the left. There is one caveat, though: It's best to keep related partitions together, so you should keep your swap partition next to the Linux partition. To do this, you'll need to either delete it and create a new one (which will then require editing /etc/fstab in Linux) or move it. In either case, you'll run into complications because your swap partition is inside an extended partition. You'll either have to resize your extended partition twice (once to grow it and again to shrink it) or you'll need to delete the extended partition (along with the swap partition) and recreate the swap partition as a primary partition. The Windows partition must be a primary partition.

If this talk of primary, extended, and logical partitions confuses you, know this: The Master Boot Record (MBR) partitioning scheme used on most x86 and x86-64 systems is limited to four primary partitions. One of these may be an extended partition, which serves as a placeholder for an arbitrary number of logical partitions. Thus, if you need more than four partitions, you can have a maximum of three primary partitions and the rest must be logical partitions inside a logical partition. Windows and some other OSes require a primary partition to boot. Linux isn't so limited, but the Ubuntu installer still puts the Linux root (/) filesystem on a primary partition if possible.

---

### Post by Rubi1200 on 2010-05-18
:)

---

