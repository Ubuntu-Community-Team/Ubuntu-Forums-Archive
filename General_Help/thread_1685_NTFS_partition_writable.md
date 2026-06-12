---
title: "NTFS partition writable?"
date: 2004-10-22
forum: General Help
---

### Post by chapterthree on 2004-10-22
Hello All,

Is it possible to make a NTFS partition (actually, a seperate physical disk, but anyway) writable?  It put the "rw" option in fstab:
```
/dev/hdb5       /mnt/data_disk  ntfs    rw,uid=1000,gid=1000    0       0
```

But when I try to modify something, I get the read-only error:
```
kev &#91;/mnt/data_disk&#93;$ chmod 755 Bills.xls
chmod&#58; changing permissions of `Bills.xls'&#58; Read-only file system
```

Any ideas?

---

### Post by Rancoras on 2004-10-22
Writing to NTFS is experimental and not included in ubuntu.  The way I understand it is that it's still rather dangerous to do.  Data loss can still occur for no apparent reason.  I would stick with read only for your NTFS partitions and create a small FAT32 partition for data sharing between windows and linux.

---

### Post by chapterthree on 2004-10-22
Ahh I see, when are they (like the NTFS Project people) gonna get writing working?  hehe

Anyway, this old NTFS partition is just data, like mp3's, etc, and I would actually like to convert it to ext3 (I will never be using Doze again).  Any tools or anything for that, or would I have to clear out that drive, format it, then copy everything back to it?

---

### Post by mint on 2004-10-22
[quote=chapterthree]But when I try to modify something, I get the read-only error:
```
kev &#91;/mnt/data_disk&#93;$ chmod 755 Bills.xls
chmod&#58; changing permissions of `Bills.xls'&#58; Read-only file system
```
[/quote]
NTFS doesn't understand Unix permissions at all (AFAIK), so your example wouldn't work even if you had write permissions.

You might want to look at [Captive NTFS](http://www.jankratochvil.net/project/captive/) [jankratochvil.net] as a way to read and write NTFS.  It creates a wrapper for the Windows NTFS DLLs on the disk so that you access the FS using "pure" Windows calls.

mint

---

### Post by Vulc on 2004-10-22
you may want to convert it to fat32 if you want windows to see it as well, I used partition magic to convert the drive, not sure if you can do it with data on it

---

### Post by LolObArO on 2004-11-29
[QUOTE=Vulc]you may want to convert it to fat32 if you want windows to see it as well, I used partition magic to convert the drive, not sure if you can do it with data on it[/QUOTE]

--> You can convert even if there are data on it .. just done it yesterday ;)

---

### Post by kahping on 2004-12-05
i often swap files with my friends who r still stuck on windows  8-[ they use ntfs on winxp

my question is: do i need windows installed in another partition to use captive? if i have the ntfs.sys + ... files on my ubuntu partition, would i be able to use captive by running them off the linux partition or is this not possible?

thanks,
kahping

---

### Post by FLeiXiuS on 2004-12-05
What I like to do is make a seperate partition for both linux and windows to share.   Use it as a storage partition.  Quite useful, thats just be though!

---

