---
title: "Second ext4 disk can only mount read only"
date: 2009-11-03
forum: General Help
---

### Post by cowchaser on 2009-11-03
I have a two disk system that used to be duel boot with XP.  I recently updated to 9.10 and got rid of the windows partition and installed Ubuntu on the first disk.  Then I cleaned off the second disk and formated it to ext4 also but now can not get it mounted read write.  I have tried all the tips I can find of this and other sites and so far nothing works.  Have changed ownership and permissions of the mount point and device file but after reboot they all change back to root.  My fstab entry is:
/dev/sdb2      /media/data     ext4         defaults                  0  0  
Any help would be appreciated, Thanks

---

### Post by Unchqua on 2009-11-03
[FONT=Verdana]AFAIK only mount point itself changes its permissions when being used by automounter or using [/FONT][FONT=Verdana]mount manually; all files inside newly mounted partition get their permissions from their own filesystem. Relevant options of mount command are: (no)user, (no)dev, (no)exec, (no)suid.[/FONT]
What's the problem anyway? You can't mount a partition as an ordinary user, only as root? Or you can't write? Use "defaults,user" option in fstab and you will be able to mount it as yourself and write onto it.

---

### Post by cowchaser on 2009-11-03
[QUOTE=What's the problem anyway? You can't mount a partition as an ordinary user, only as root? Or you can't write? Use "defaults,user" option in fstab and you will be able to mount it as yourself and write onto it.[/QUOTE]

I am not able to write to the empty disk as a normal user.  I was able to copy files as root to it and the write to the copied folders as normal user.  Maybe it is suppose to work this way but seems strange.

---

### Post by Unchqua on 2009-11-04
After some experiments I came into this on my Ubuntu 8.04: no matter what ownership and permissions have both device and its corresponding mount point, what really matters is who created a filesystem in the first place. If I do mke2fs from ordinary user, then even if this filesystem (not a real partition but a file made with dd on disk, then formatted with mke2fs) has root:root ownership and so mount point, and even if mount command invoked under root accout, resulting device has an ownership of that ordinary user. This is something I had contrary belief until now.
Can you recreate your desired ext4 partition from ordinary user, not root?

---

### Post by vdr60 on 2009-12-22
I have the same problem: I want create an ext4 partition on a second internal disk. If I create it with gparted when mounted it is read only.

How do you used mke2fs without root privilege? I tryed and it fails asking root....

---

