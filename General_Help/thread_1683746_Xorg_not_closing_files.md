---
title: "Xorg not closing files??"
date: 2011-02-08
forum: General Help
---

### Post by spacetree on 2011-02-08
Hi.

Recently, gnome has been warning me about low disk space, always less than 1.5GiGs. 

The problem is, baobab (disk usage analyzer) tells me that there are something like 50GiG free. I am sure that I have the free space ( I can write big files ) but the system keeps reporting low disk space. Even ```
df -h
``` looks wrong:


```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda1     ext4    221G  209G  638M 100% /
none      devtmpfs    2.0G  272K  2.0G   1% /dev
none         tmpfs    2.0G  1.9M  2.0G   1% /dev/shm
none         tmpfs    2.0G  328K  2.0G   1% /var/run
none         tmpfs    2.0G     0  2.0G   0% /var/lock
none       debugfs    221G  209G  638M 100% /var/lib/ureadahead/debugfs

```

Wandering in some other thread, someone pointed out that some program may be deleting files ... but not closing them, and the offending program can be fount with  ```
sudo lsof -s | grep DEL | sort -rnk 7,7
``` ,which gives a wall of results like these
```

Xorg      1334                root  DEL       REG                0,4                 8573 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8572 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8571 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8570 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8569 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8568 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8567 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8566 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8565 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8564 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8563 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8562 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8561 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8560 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8559 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8558 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8557 /drm mm object
Xorg      1334                root  DEL       REG                0,4                 8556 /drm mm object

```

Perhaps Xorg is having a very bad behavior?? What can I do to force it close the files , or whatever else that can give me back the hard disk space ... working is unpractical since most applications (gnome apps) think that there is no space left on the device.

Thanks in advance.

EDIT:

My sistem is Ubuntu 10.10 64bit, with all the upgrades until today (proposed updates enabled)
XORG INFO:


X.Org X Server 1.9.0
Release Date: 2010-08-20
X Protocol Version 11, Revision 0

Also something seems wrong with the following info

```

saeioul@saul-satellite:~$ df -ih
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda1                15M    446K     14M    4% /
none                    493K     840    492K    1% /dev
none                    495K      17    495K    1% /dev/shm
none                    495K      68    495K    1% /var/run
none                    495K       1    495K    1% /var/lock
/dev/sdb5               4.2M      32    4.2M    1% /media/Data backup
/dev/sdb1               480K     872    479K    1% /media/Docs and books
saeioul@saul-satellite:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             221G  209G  1.1G 100% /
none                  2.0G  296K  2.0G   1% /dev
none                  2.0G  2.3M  2.0G   1% /dev/shm
none                  2.0G  360K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
/dev/sdb5              66G   40G   23G  64% /media/Data backup
/dev/sdb1             7.4G 1017M  6.0G  15% /media/Docs and books

```

---

