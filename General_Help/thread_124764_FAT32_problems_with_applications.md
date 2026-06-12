---
title: "FAT32 problems with applications"
date: 2006-02-02
forum: General Help
---

### Post by anodizer on 2006-02-02
Hi, I'm using ubuntu as my primary OS for the last month and I'm really excited. I can't wait for the Dapper Drake release.
However, I have this problem, I made a fat32 partition to use as storage. The fstab line looks like this: ```
/dev/sdb5 /mnt/media vfat user,iocharset=utf8,fmask=0111,dmask=0000   0   0
```
I can read and write normally, but when I set this mounted folder as the default save directory in my bittorrent client (azureus and bittornado) it can't write. I get an error like "Operation not permitted, cannot allocate files". I chanched the permissions of the mnt and media folder to 777 but it made no difference. Also I'm trying to change the owner for the mounted folder "media" (I did it already for the mnt folder) and I can't, probably because the hdd is already mounted. How can I change it through the fstab file, if it is necessary of course.
Any help will be much appreciated, thanks in advance.

---

### Post by lamego on 2006-02-02
You need to use umask=000 on the mount options to give access to all users.

---

### Post by kverde on 2006-02-02
Actually,  I just had this problem in Azureus and solved it by going to tools --> options --> file --> [I]"Enable incremental file creation." [Required for fat32 under linux] 

[Info Here]("http://azureus.aelitis.com/wiki/index.php/FAT32_partition_under_Linux")
[/I]

---

### Post by anodizer on 2006-02-02
Yes, that worked.\\:D/ 
Thanx a lot

---

