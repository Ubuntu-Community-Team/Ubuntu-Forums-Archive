---
title: "Deleting my Windows partition."
date: 2010-03-19
forum: General Help
---

### Post by cdysthe on 2010-03-19
Hi,

I have a small primary Windows partition at the beginning of my drive right before my /home partition (also a primary partition). I would like to delete the Windows partition since I'm never on there anymore and expand the /home partition to use the freed up space. I know how to do this with gparted, but what I do not know is what to do with grub2 afterwards making sure I can boot into my Ubuntu install. Could someone please let me know what I have to do after I have deleted the Windows partition and expanded my /home partition before I reboot making sure I can boot as normal having the Windows grub menu entry removed and Ubuntu boot normally?

I'm running Ubuntu 9.10 64 bit.

---

### Post by srs5694 on 2010-03-19
In theory, no changes should be required, since your Linux root (/) and/or /boot (if present) partition(s) will either be primaries with numbers that shouldn't be affected by this change or are logical partitions, again with numbers that won't be affected by this change.

In practice, I can't guarantee that I'm right, though. I'm not an expert on how GParted handles partition numbering in all situations, and given my limited knowledge, I can't promise that it won't change partition numbers even when you don't ask it to do so. To be safe, you might want to print or copy the output of a "sudo fdisk -l /dev/sda" command before you make any changes, and mark which Linux partitions are which on your printout. After you make your changes in GParted, run this command again and compare the results to be sure your Linux partition numbers haven't changed. Most stock Ubuntu installations use UUID numbers rather than partition numbers in critical system files, such as /etc/fstab. I'm not sure if you'd need to edit your GRUB configuration (/boot/grub/grub.cfg), since my own system is rather unusual in that I use LVM for most everything, so I've got LVM filename references in there for some features rather than partition references. Likewise, it's conceivable that the UUID number on your /home partition will change, although I ran some tests when this issue came up in another thread and I found that GParted did *not* change UUID numbers when resizing ext3 filesystems.

---

