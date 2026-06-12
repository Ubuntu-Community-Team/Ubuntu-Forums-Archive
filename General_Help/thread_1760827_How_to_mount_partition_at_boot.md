---
title: "How to mount partition at boot ?"
date: 2011-05-17
forum: General Help
---

### Post by sid.mallya on 2011-05-17
Hey guys ! I keep a separate partition for files and folders which I absolutely need for my college work. (I do this because I had accidentally wiped my /home partition while upgrading Linux before)

Anyway, I want to know how to mount this partition at boot automatically .. I know I am supposed to append an entry to /etc/fstab but I am a lil apprehensive about doing this without a go-ahead from users here.

"fdisk -l" yields this ->

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009901e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4181    33583851   83  Linux
/dev/sda2           60054       60802     6008833    5  Extended
/dev/sda3           27506       60053   261441810   83  Linux
/dev/sda4            4182       27505   187350030   83  Linux
/dev/sda5           60054       60802     6008832   82  Linux swap / Solaris
```

I want to mount the /dev/sda3 at partition. As seen here, this is **NOT** a NTFS partition.

How do I go about it ?

---

### Post by Wim Sturkenboom on 2011-05-17
edit /etc/fstab

```

fortyfourgalena@desktop-01:~$ cat /etc/fstab 
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=c7f8f5d5-d24e-43ac-9b7f-2b31804a58ac /               ext3    errors=remount-ro 0       1
UUID=ba587de2-a984-4d69-9070-17b17aeed06b /home           ext3    defaults        0       2
UUID=0173d67a-bb5c-43bf-91c8-1fe03c5ff641 none            swap    sw              0       0
# WimS
**/dev/sdb1 /photos ext3 defaults 0 2**
fortyfourgalena@desktop-01:~$ 

```
Something like the bold line above; I did add a HD dedicated to photos (/dev/sdb), so created a directory /photos that is used as mountpoint and mount the partition on it.

Note that you might not have a trash for that partition when doing it this way; I'm still trying to figure out how to get it for that partition.

You can also use UUIDs, but I'm not sure how to find them. The UUIDs that you see are from a standard install.

---

### Post by sisco311 on 2011-05-17
EDIT: Wim Sturkenboom beat me to it. :)

First you need to find the UUID of the partition and the type (ext3 or ext4).

The following command will print the information you need:
```
sudo blkid -o udev -c /dev/null /dev/sda3
```

Then open the fstab file:
```
gksu gedit /etc/fstab
```

and add this entry at the end of the file:
```
UUID=[color=red]xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx[/color]   [color=green]/mount/point[/color]    [color=blue]type[/color]    relatime    0    2
```

Where
[color=red]xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx[/color] is the UUID you get from the previous command

[color=green]/mount/point[/color] is the mount point. For example: /media/data or /home/user/data.

and

[color=blue]type[/color] is the type of the partition (e.g. ext4).

After you save the file, make sure that the mount point exists:
```
**sudo** mkdir -p [color=green]/mount/point[/color]
```

Note: If you create the mount point in your home directory, then you don't have to use **sudo**.

You can mount the partitions listed in fstab with:
```
sudo mount -a
```

---

### Post by sid.mallya on 2011-05-17
Thanks guys ! Worked brilliantly ! :)

---

