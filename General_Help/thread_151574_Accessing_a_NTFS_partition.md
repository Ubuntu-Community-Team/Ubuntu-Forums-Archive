---
title: "Accessing a NTFS partition"
date: 2006-03-28
forum: General Help
---

### Post by AmonSacha on 2006-03-28
Is it possible to access a NTFS partition from Ubuntu? There is no OS installed on it, it just has my music library on it and a few bittorrented things.

If so, how?

Thanks in advance
Ian

---

### Post by yota on 2006-03-28
Hi,

not to bug you, but this question had been answered millions of times... be kind and try to search the forum and the wiki before posting!
Still friends? ;) Ok, i hope so and I'll point you directly to the answer:

[https://wiki.ubuntu.com/MountNtfsOnBoot](https://wiki.ubuntu.com/MountNtfsOnBoot)

If you want to mount the partition just one time you can:
```

sudo mount -t ntfs /dev/hdXX /path/to/a/folder/of/your/choice

```
from a command line.
type "man mount" for more information.

Hope this helps!

---

### Post by nirtal on 2006-03-28
Yes you can!

First type this command in a terminal to locate the NTFS partition
```
sudo fdisk -l
```

Then it says something like

```

Disk /dev/sda: 250,0 GB, 250059350016 byte
240 huvuden, 63 sektorer/spår, 32301 cylindrar
Enheter = cylindrar av 15120 × 512 = 7741440 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833       29321   215376840    7  HPFS/NTFS
/dev/sda3           29322       32301    22528800    5  Utökad
/dev/sda5   *       29322       32227    21969328+  83  Linux
/dev/sda6           32228       32301      559408+  82  Linux växling / Solaris

Disk /dev/sdb: 250,0 GB, 250059350016 byte
240 huvuden, 63 sektorer/spår, 32301 cylindrar
Enheter = cylindrar av 15120 × 512 = 7741440 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sdb1               1       32166   243174928+   7  HPFS/NTFS


```

Now you see that I have 2 NTFS partitions (To the right it says "HPFS/NTFS" on them)

/dev/sda2
/dev/sdb1

I have SATA disks but if you have IDE disk then it maybe is /dev/hda instead of /dev/sda

After that you edit fstab
```
sudo gedit /etc/fstab
```

and add something like this
```
[/dev/sda2	/media/windows	ntfs users,owner,ro,umask=000 0 0/CODE]

Then make the mounting directory
[CODE]sudor mkdir /media/windows
```

Then all you need to do is type 1 command moore to mount the partitions
```
sudo mount -a
```

Now there should be a icon on your desktop named windows

This make you to be enable to read and watch all of your files on the NTFS partition but you can't write things on it. What I know there is possible to make your NTFS writeble but it's very risky and could damage your NTFS partitions

---

### Post by AmonSacha on 2006-03-28
Thank you very much, sorry for not searching, I was kinda panicked at the time.

Thanks for the help

Ian

---

