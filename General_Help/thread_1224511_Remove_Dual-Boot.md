---
title: "Remove Dual-Boot"
date: 2009-07-27
forum: General Help
---

### Post by Flexico on 2009-07-27
I've been dual-booting with Windows XP for a while now, and I've finally decided to do away with it and dedicate my whole hard drive to Ubuntu. What's the best way to do this? I was going to use my LiveCD to just repartition the drive, but I'm too afraid of Error 22 if I do something wrong.

---

### Post by Diabolis on 2009-07-27
You should be find, just resize your partition. What I've done in the past is overwrite the windows partition with a "storage" partition and then delete the windows entry from the menu.lst file.
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by merlinus on 2009-07-27
Probably the easiest solution is to format your existing xp partition as ext3 using gparted, mount it as /data in /etc/fstab, and use it for storage, music, photos, and such.

Then delete the xp entry from /boot/grub/menu.lst.

---

### Post by metalf8801 on 2009-07-27
> **Flexico said:**
> I've been dual-booting with Windows XP for a while now, and I've finally decided to do away with it and dedicate my whole hard drive to Ubuntu. What's the best way to do this? I was going to use my LiveCD to just repartition the drive, but I'm too afraid of Error 22 if I do something wrong.

I would just shrink the XP partition but not remove unless you can the CDs to reinstall windows because from time to time you might need to use Windows. Its sad but true that there are things you just can't do in Ubuntu. oh and to shrink the XP partition I would use GParted  
[http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted)

---

### Post by Flexico on 2009-07-27
> **metalf8801 said:**
> I would just shrink the XP partition but not remove unless you can the CDs to reinstall windows because from time to time you might need to use Windows. Its sad but true that there are things you just can't do in Ubuntu. oh and to shrink the XP partition I would use GParted  
[http://distrowatch.com/table.php?distribution=gparted](http://distrowatch.com/table.php?distribution=gparted)

Well, I plan to use VirtualBox for any Windows needs. XD

---

### Post by Flexico on 2009-07-27
OK, I did it, but there was some kind of error while re-partitioning. Now there is just my Linux partition (and swap) which boots up OK *collapses with relief*, but it says that there is 98.7 GB used (in gparted), but in the filesystem it only picks up 35.3 GB, which is about what it should be.

What happened? And how do I get my whole hard drive back?

---

### Post by joeinbend on 2009-07-27
I'm not 100% sure, but I think you just need to expand your file system to the available free space, using resize2fs

---

### Post by Flexico on 2009-07-27
> **joeinbend said:**
> I'm not 100% sure, but I think you just need to expand your file system to the available free space, using resize2fs

The filesystem is expanded to the free space, but it is registering as being mostly full, when it's not.

---

