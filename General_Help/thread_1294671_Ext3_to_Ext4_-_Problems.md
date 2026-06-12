---
title: "Ext3 to Ext4 - Problems"
date: 2009-10-18
forum: General Help
---

### Post by zzzBrett on 2009-10-18
I (unfortunately) attempted to upgrade my partition from ext3 to ext4.  I was in my desktop (partitions mounted), logged in to KDE.

I ran:
(from online tutorial)
```
sudo tune2fs -O extents,uninit_bg,dir_index /dev/sda5
```

Then:
```
sudo fsck -pf /dev/sda5
```

It came back and said doing that while mounted could damage the partition, lose files, or something along the lines of that.  So I decided to unmount the partition.  After a 'umount' attempt, it said the device was busy.  So I ran

```
umount -l /dev/sda5
```

Then again attempted to run

```
sudo fsck -pf /dev/sda5
```

but it still didn't work (I forgot the exact error).  So I ended up restarting my computer (big mistake).  Now I can't boot into any graphical interface, I try to go into the recovery option on grub and I get all kinds of errors; it asks for a root login password, but my password does not work, i have the option to press control+D, but I can do that forever and new errors will keep coming up.

So I tried to boot from a live CD -- didn't work, just went to a black screen.  Also tried booting from CD and doing a fresh install of kubuntu / ubuntu, doesn't work either.  So basically I am stuck.

I realize recovering my files may be a lost cause (i have the important ones backed up), but I can't even get back to any kind of working condition.

What do i do?

---

### Post by zzzBrett on 2009-10-19
I fixed the problem by reinstalling the root with the alternate installer instead of the live / regular installer.  I specified to use the partition that I upgraded (above) to ext4 as /home and as ext4, and it just worked fine, so I assume the upgrade actually went OK.  Not sure exactly what went wrong, but all fixed now!

---

