---
title: "Has the recent pmount update killed USB rw?"
date: 2006-03-27
forum: General Help
---

### Post by open_sauce on 2006-03-27
Hi all,

I've got an mp3 player that's simply a removable storage device that auto-mounts from /dev/sda to /media/usbdrive.

All has beeen going well and I have been loading my favourite tunes and casts from both XP and Ubuntu -- until the last update. I spent 2 hours chmodding, sudo chmodding and fstab editing -- all with no luck.

I did notice that the recent Ubuntu update (that seems to have caused this problem) mentioned an update to allow mounting USB as a 'normal' user via pmount. Could this be the source of my trouble?

When mounted, it says that the file system belongs to my default Ubuntu account, is a VFAT type, and is a read-only file system. I don't know what it used to say, because, well, it just worked!

Any tips/advice muchly appreciated.

[I have tried editing /etc/fstab with various combinations of umask, uid, gid, etc etc from these forums, but nothing has worked, so I removed the usb fstab line and am now back to my original fstab (hda1, etc) and the file permissions problem.]

In the meantime, I'm forced to use XP to load my songs. :-k

---

### Post by open_sauce on 2006-03-28
bump

---

