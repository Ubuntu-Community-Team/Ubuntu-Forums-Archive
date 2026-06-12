---
title: "How to make an NTFS partition"
date: 2010-03-01
forum: General Help
---

### Post by DeMus on 2010-03-01
Hi,

I use jaunty 64 bits on a software raid 0. My partitions are:
disk a:
sda1 /boot ext4 (no raid)
sda2 /     ext4 md0
sda3 /home ext4 md1

disk b
sdb1 not used   (no raid)
sdb2 /     ext4 md0
sdb3 /home ext4 md1

Now I need to make an NTFS partition. The reason is my mediaplayer, which I use to play HD movies on my TV, can not read ext4 disks.
How would I do such a thing? I tried using gparted but have no idea how to make room for a new partition on a raid 0.
I can reduce the size of the md1 raid to make room for the new partition if I new how.
Who can help me with this?

---

### Post by [Re] Smile on 2010-03-01
Have you checked the [GParted documentation]("http://gparted.sourceforge.net/larry/resize/pdf/Resizing.pdf") ?

[COLOR=Gray]** If I remember right, NTFS's can be created only from the LiveCD.[/COLOR]

---

### Post by DeMus on 2010-03-01
> **'[Re] Smile said:**
> Have you checked the [GParted documentation]("http://gparted.sourceforge.net/larry/resize/pdf/Resizing.pdf") ?

[COLOR=Gray]** If I remember right, NTFS's can be created only from the LiveCD.[/COLOR]

Thank you for your fast answer, but I read nothing about Raid. I know how Gparted works, but have no ideas what to do to reduce a raid partition and after that create a new raid NTFS partition.
I need the raid for a faster datastream.

---

### Post by DeMus on 2010-03-02
No one? Come on, this can't be the first time this problem comes up.

---

### Post by darolu on 2010-03-02
Installing all this should do the trick:
```
sudo apt-get install ntfs-3g ntfs-config ntfsprogs
```
After that gparted (and parted) *should* be able to create ntfs partitions.

Oh yeah for the raid thing: [http://www.gnu.org/software/parted/manual/html_chapter/parted_7.html](http://www.gnu.org/software/parted/manual/html_chapter/parted_7.html)

---

### Post by rnerwein on 2010-03-03
hi
have a look at "cfdisk". i have never used it for raid. but as far i know cfdisk is able to handle raid.
it's a very nice tool !!
ciao

---

### Post by DeMus on 2010-03-09
I added a separate hard disk into my computer and through a bootable Gparted disk I was able to format the drive in NTFS format. I can mount it by hand using:
```
sudo ntfs-3g /dev/sdc1 /media/Video
```
I can use it, that's no problem. I just wish to mount it automatically when the computer boots. I have tried to do that in fstab but that didn't work. Then I wrote the above code in a script and tried to start it when the computer boots, but it doesn't do that.
Now I start the script by hand and the disk mounts.

The script contains this code:
```
#!/bin/sh
sleep 5
sudo ntfs-3g /dev/sdc1 /media/Video
```

How can I automount an NTFS disk in my computer?

---

### Post by oldefoxx on 2010-03-09
You can use /etc/fstab for mounting any partition, including fat32 and ntfs.  It's often in what options you elect as it is being mounted.  Some good choices are default,rw,user.  This will mean that the user is allows access, and you can do read and writes to it.  If you specify ro instead of rw, you only have read access.  Though you would not normally store Linux-compatible executable files in an ntfs partition, you can add exec to the fstab entry.

LiveCD's version of partitioner allows for NTFS, but a better choice might be gparted.iso, which you can then boot to.  There are some features with gparted.iso that are not apparent with the other versions, such as copying one partiton over into another.  Not sure if this works between drives though.

---

### Post by DeMus on 2010-03-09
> **oldefoxx said:**
> You can use /etc/fstab for mounting any partition, including fat32 and ntfs.  It's often in what options you elect as it is being mounted.  Some good choices are default,rw,user.  This will mean that the user is allows access, and you can do read and writes to it.  If you specify ro instead of rw, you only have read access.  Though you would not normally store Linux-compatible executable files in an ntfs partition, you can add exec to the fstab entry.

LiveCD's version of partitioner allows for NTFS, but a better choice might be gparted.iso, which you can then boot to.  There are some features with gparted.iso that are not apparent with the other versions, such as copying one partiton over into another.  Not sure if this works between drives though.

Thank you for your answer. One question:
what would be the syntax when using fstab? I know the drive is called sdc, has 1 partition sdc1 and I also know the UUID.
What would I have to write in fstab to make it work?

---

### Post by J_Stanton on 2010-03-09
> **DeMus said:**
> Thank you for your answer. One question:
what would be the syntax when using fstab? I know the drive is called sdc, has 1 partition sdc1 and I also know the UUID.
What would I have to write in fstab to make it work?

 ```
/dev/sdc1 /mountpoint/sdc1 ntfs-3g defaults 0 0
```

---

### Post by GeneGrady on 2010-03-09
I just use the windows cd to format the NTFS partition and when it restarts change the CD.

Good luck..

Gene

---

### Post by DeMus on 2010-03-09
> **J_Stanton said:**
> ```
/dev/sdc1 /mountpoint/sdc1 ntfs-3g defaults 0 0
```

Thanks, it works. One last question: what do the last 2 zero's do?

---

