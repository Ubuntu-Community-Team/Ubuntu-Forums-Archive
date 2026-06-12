---
title: "Auto mount all drives"
date: 2010-06-16
forum: General Help
---

### Post by elliotn on 2010-06-16
How can I auto mount all my drive at start up, I want them to be auto mounted.

---

### Post by elliotn on 2010-06-16
Any1

---

### Post by TeoBigusGeekus on 2010-06-16
You need to edit your [fstab file]("http://ubuntuforums.org/showthread.php?t=283131").

---

### Post by amedac on 2010-06-16
If your drives are formated in NTFS then install NTFS Configuration tools from Ubuntu software center

---

### Post by Morbius1 on 2010-06-16
During the initial install of Ubuntu you are given the opportunity to mount all your partitions if you choose the manual partitioning option. When Ubuntu mounts them in [COLOR=Blue]/etc/fstab[/COLOR] it uses these templates depending on the filesystem being used:

> UUID=f7927995-b098-42be-ada0-987857f5177a [COLOR=DarkGreen]/DATA[/COLOR]           [COLOR=Blue]ext4[/COLOR]    defaults        0       2
UUID=66E4DC83E4DC56C1 [COLOR=DarkGreen]/WinBACKUP[/COLOR] [COLOR=Blue]ntfs [/COLOR]   defaults,nls=utf8,umask=007,gid=46 0       0
UUID=C4DB-C1B0  [COLOR=DarkGreen]/WinJ [/COLOR]     [COLOR=Blue]vfat[/COLOR]    utf8,umask=007,gid=46 0       1I generally modify these a bit depending on my needs but for the most part this it will work as is.

To find the correct UUID number for each partition use the following command:
```
sudo blkid -c /dev/null
```You will also need to create the mount points, using the above as examples:
```

sudo mkdir [COLOR=DarkGreen]/DATA
[/COLOR]sudo mkdir [COLOR=DarkGreen]/WinBACKUPS[/COLOR]
sudo mkdir [COLOR=DarkGreen]/WinJ[/COLOR]

```

---

