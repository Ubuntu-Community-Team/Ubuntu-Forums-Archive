---
title: "no free space on disk"
date: 2010-01-02
forum: General Help
---

### Post by PunkSale on 2010-01-02
I have a partition (ext3) on my disk used for storing personal files, but I am unable to copy anything on it "normal" way ("not enough free space" error), only with "sudo cp".
There apparently is some free space on it (according to GParted, 6.25 GiB is unused), but I want to copy files using the "normal" way too.

Help, please? :)

---

### Post by Leppie on 2010-01-02
Hi and welcome to the community.

how did you mount this partition?

---

### Post by PunkSale on 2010-01-02
Thank you. :)

Places -> Clicking on the partition -> entering root password

---

### Post by Leppie on 2010-01-02
> **PunkSale said:**
> Places -> Clicking on the partition -> entering root password
check the folder and file permissions in nautilus, i think they are all set to root.
did you add yourself to the fuse group? that would allow your account to mount partitions (you still will be prompted for your password, but you will should obtain read/write access). Go to System>Administration>Users and Groups, unlock the applet by clicking the keys icon and entering your password, select your account and click properties, go to the User Privileges tab, select "Mount user-space filesystems (FUSE)" click ok, close the applet. you probably have to log out and in again.

---

### Post by PunkSale on 2010-01-02
> **Leppie said:**
> check the folder and file permissions in nautilus, i think they are all set to root.
did you add yourself to the fuse group? that would allow your account to mount partitions (you still will be prompted for your password, but you will should obtain read/write access).

I am the owner and have permissions, and I can access and delete files and folders. But no free space when copying. Even when I try with "sudo nautilus"...
And yes, I'm in the FUSE group.

---

### Post by Windsurfer619 on 2010-01-02
There is sometimes a percentage of a disk reserved for root, so you can still use the disk in emergency situations. I would recommenced either deleting something off the disk, or reducing the reserved space.  If you wish to reduce the reserved space, you'll have to google that on your own... I've never had to do it  :(

---

### Post by Leppie on 2010-01-02
> **PunkSale said:**
> But no free space when copying. Even when I try with "sudo nautilus"...
so you can copy with "sudo cp" but not in nautilus with root permissions?

---

### Post by PunkSale on 2010-01-02
> **Windsurfer619 said:**
> There is sometimes a percentage of a disk reserved for root, so you can still use the disk in emergency situations. I would recommenced either deleting something off the disk, or reducing the reserved space.  If you wish to reduce the reserved space, you'll have to google that on your own... I've never had to do it  :(

Never heard of it before. :D But that was it, thank you very much. :D

sudo tune2fs -m 1 /dev/sdXX (that's number 1 -> percentage of reserved space, not L )

---

### Post by fancypiper on 2010-01-12
You might want to clean up your system.

[HOWTO: Recover Lost Disk Space](http://newyork.ubuntuforums.org/showthread.php?p=7053432)

---

