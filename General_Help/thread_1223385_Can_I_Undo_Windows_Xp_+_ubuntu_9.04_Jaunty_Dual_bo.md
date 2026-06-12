---
title: "Can I Undo Windows Xp + ubuntu 9.04 Jaunty Dual boot?"
date: 2009-07-26
forum: General Help
---

### Post by Cfhs_1 on 2009-07-26
Hello everyone,



       I have my system set up to dual boot Win XP SP3, And Ubuntu 9.04 Jaunty as the title says, but now im running a little low on disk space so i'd like to do away with Win XP, who needs it anyway?, and combine that partition with my Ubuntu partition all without disturbing my ubuntu installation. (It took me forever to get it just perfect) Is there any way to pull this off? Thanks ahead of time for any help!

:D

---

### Post by merlinus on 2009-07-26
An easier way would be to format your existing xp partition as ext3 and mount it as /data (or whatever name you like).  Then you can use it for all sorts of files, e.g. music, photos.

---

### Post by Cfhs_1 on 2009-07-26
> **merlinus said:**
> An easier way would be to format your existing xp partition as ext3 and mount it as /data (or whatever name you like).  Then you can use it for all sorts of files, e.g. music, photos.

Yea I thought about that, but I'd really like to somehow combine the partitions so I don't have to deal with mounting and un-mounting the other partition...

:(

---

### Post by merlinus on 2009-07-26
It is very easy to have the new partition automount by adding an entry for it in /etc/fstab.

---

### Post by Bucky Ball on 2009-07-26
Run windows installation disk and delete the windows partition.

Run the Live CD and open Partition Editor (Gparted). Extend your partition into the empty space. You may be able to do the whole procedure using Gparted but not sure if it will delete NTFS partitions (never tried).

I advise you back up anything you don't want to lose before attempting this, just in case. The reason you must do this from the Live CD is that the partitions you want to manipulate must be UN-mounted to work on (therefore you can't do this from within a running install of Ubuntu as the drive is obviously mounted).

Good luck. :)

---

### Post by merlinus on 2009-07-26
This will work, unless linux is in an extended partition.  Then you will have to first delete the old xp partition, grow the extended partition to include that space, and then grow the linux partition as well.

In order to do this, all space must be touching one another.

Post results of

```
sudo fdisk -l
```

and we can see how your partitions are set up.

---

### Post by Cfhs_1 on 2009-07-26
> **Bucky Ball said:**
> Run windows installation disk and delete the windows partition.

Run the Live CD and open Partition Editor (Gparted). Extend your partition into the empty space. You may be able to do the whole procedure using Gparted but not sure if it will delete NTFS partitions (never tried).

I advise you back up anything you don't want to lose before attempting this, just in case. The reason you must do this from the Live CD is that the partitions you want to manipulate must be UN-mounted to work on (therefore you can't do this from within a running install of Ubuntu as the drive is obviously mounted).

Good luck. :)


Thanks!! this worked perfectly! ( I only had to use the live CD) Thank you soo much!! :):D

---

### Post by Cfhs_1 on 2009-07-26
thanks!!!!!!!!!!

---

### Post by Bucky Ball on 2009-07-27
You are more than welcome! I like it when a plan works out. ;-)

---

