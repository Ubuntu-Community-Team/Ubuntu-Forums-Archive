---
title: "NTFS Drive not mounting upon reboot"
date: 2010-10-17
forum: General Help
---

### Post by takiama on 2010-10-17
So, I used Wubi to install Ubuntu 10.10 onto my laptop alongside Windows 7.  I need to access my windows harddrive, however, so I used NTFS Configuration Tool to mount the drive.  However, whenever I reboot, it fails to mount and I actually have to go back into NTFS Config Tool, delete the old mount, and remount it.  This is tedious.  My /etc/fbstab file looks as follows:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda2	/media/windows	ntfs-3g defaults,nosuid,nodev,locale=en_US.utf8	0	0
 
/host/ubuntu/disks/swap.disk	none	swap	loop,sw	0	0
```

---

### Post by coffeecat on 2010-10-17
You do not need an /etc/fstab entry to access the Windows partition in a Wubi install. You can find it at /host. Details here:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20access%20the%20Windows%20drives?)

If you don't want to navigate to it every time, open a Nautilus window, go to /host and add a bookmark from the bookmarks menu. This will add an entry in the Places menu. Or you can add a desktop launcher with "nautilus /host". 

I think the reason that it fails to mount to /media/windows is that the system is over-riding your fstab entry. I suggest you delete the fstab line. If you really want the Windows C: drive appearing in /media/windows, simply make /media/windows a symlink linking to /host.

---

### Post by takiama on 2010-10-17
Wow, that was a blatant oversight on my part to miss /host.  I created a symlink to /media/windows because I had stuff pointing there from previous mounts, and it works wonderfully.  Thanks much.

---

