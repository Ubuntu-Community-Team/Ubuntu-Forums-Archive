---
title: "No Boot after Power Down"
date: 2012-05-22
forum: General Help
---

### Post by mcman56 on 2012-05-22
My system froze and would not allow a reboot or shut down command so I manually powered off.   When I power up, it shows that it can not find multiple files like root/dev, sys, proc and says no sbin/init.  It seems to default to something called busybox ash with an initramfs prompt.  Typing help brings up a bunch of possible commands but I am lost.  Is there a method to recover?

---

### Post by mcman56 on 2012-05-23
The hard drive passes the bios disk test.  I can boot on the CD.  fdisk shows it trying to boot at the correct location, sda1.   I can see the file system but it says I do not have permission to look in \boot.

---

### Post by oldfred on 2012-05-23
If systems seems to lock up remember the elephants. Otherwise you may corrupt data and have to run e2fsck.

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

#From liveCD so everything is unmounted,swap off if necessary, change example shown with sdb1 to your partition(s)
# To see ext3 or ext4 partitions to use 
 sudo blkid -c /dev/null -o list
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by mcman56 on 2012-05-24
Initially that command returned odd "can't do" messages.  Then it suggested the e2fsck without the following characters.  That worked.  Thanks

---

