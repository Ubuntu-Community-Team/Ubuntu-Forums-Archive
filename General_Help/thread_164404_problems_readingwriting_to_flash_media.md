---
title: "problems reading/writing to flash media"
date: 2006-04-22
forum: General Help
---

### Post by jnev on 2006-04-22
I'm having a problem. whenever I plug in any form of flash media (flash drive, or memory card into card reader) in Ubuntu, it auto-mounts fine, but it's always hit-or-miss as to whether it will read or write to it correctly (most of the time it doesn't work right). I can copy something to the media but it doesn't show up when I view it on another computer. many times it uses up space on the media but I can't view it anywhere. even if i unplug the media form my computer, then plug it back in, I won't be able to see it. also, it sometimes misquotes the amount of memory available, so when I really have 200mb left, it says 40mb left so I can't copy some fiiles to it.

any help would be much appreciated.
thanks!

---

### Post by aysiu on 2006-04-22
Can you plug your flash media in and then go to Applications > Accessories > Terminal and copy and paste these commands in? ```
sudo fdisk -l
df -h
cat /etc/fstab
``` Please post the output here.

---

### Post by jnev on 2006-04-22
```
jnev@jnevPC-linux:~$ sudo fdisk -l
Password:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          65        9726    77609983+   7  HPFS/NTFS
/dev/sda2               1          64      514048+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2550    20482843+  af  Unknown
/dev/sdb2   *        2551        3825    10241437+  83  Linux
/dev/sdb3            5902        9726    30724312+   7  HPFS/NTFS
/dev/sdb4            3826        5100    10241437+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           16621       25498    71312535    c  W95 FAT32 (LBA)
/dev/sdc2           25499       36483    88237012+   c  W95 FAT32 (LBA)
/dev/sdc3   *           1       16620   133500118+   c  W95 FAT32 (LBA)

Partition table entries are not in disk order

Disk /dev/sdh: 519 MB, 519569408 bytes
129 heads, 32 sectors/track, 245 cylinders
Units = cylinders of 4128 * 512 = 2113536 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1         246      507376    4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 128, 32) logical=(245, 106, 32)
jnev@jnevPC-linux:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2             9.7G  3.7G  5.5G  41% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-10-386/volatile
/dev/sda1              75G   69G  5.5G  93% /media/Windows
/dev/sdc1              68G   53G   16G  78% /media/Movies
/dev/sdc2              85G   67G   18G  80% /media/Misc
/dev/sdc3             128G  122G  5.6G  96% /media/Music
/dev/sdh1             496M  378M  119M  77% /media/FLASH DRIVE
jnev@jnevPC-linux:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/Windows  ntfs    ro,auto,uid=1000,gid=1000 0 0
/dev/sdc1       /media/Movies   vfat    umask=000,rw    1       0
/dev/sdc2       /media/Misc     vfat    umask=000,rw    1       0
/dev/sdc3       /media/Music    vfat    umask=000,rw    1       0
/dev/sda2       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

```

---

### Post by aysiu on 2006-04-22
Ordinarily, I'd tell you to add a line in your /etc/fstab for /dev/sdh1, but this line in the *sudo fdisk -l* output seems weird to me: ```
Partition 1 has different physical/logical endings:
     phys=(249, 128, 32) logical=(245, 106, 32)
``` I've never seen that before... maybe that's the source of your problems...?

---

### Post by jnev on 2006-04-23
so what should I do about it...? it's a 512mb sony flash drive...

---

### Post by sinkxdie on 2006-04-23
Was the file system NTFS? If so, you know you can't write NTFS easily.

---

### Post by jnev on 2006-04-23
no, it's fat32 or fat16, whatever most flash drives are formatted in...

---

### Post by Sutekh on 2006-04-23
jnev, is this problem local to the sony flash drive or does this happen with other devices?

---

### Post by kwn12 on 2006-04-23
[quote=Sutekh]jnev, is this problem local to the sony flash drive or does this happen with other devices?[/quote]

I have the same problem with my Lexar Jumpdrive (512mb.)

---

### Post by Sutekh on 2006-04-23
[QUOTE=kwn12]I have the same problem with my Lexar Jumpdrive (512mb.)[/QUOTE]
Is your problem that you can't mount it correctly or that you have different physical/logical partition endings?

---

### Post by robglinka on 2006-04-23
It could be a very simple problem as well, if you unplug the USB drive while it is writing to it, you would corrupt the file it is writing and experience the problems you are having. 

I would suggest waiting until the file completes writing and then unmounting the drive manually before removing it.

-rob

---

### Post by jnev on 2006-04-24
it happens to my flahs drive and whatever other memory cards (secure digital and microdrive compact flash) I plug into my card reader.

---

### Post by jnev on 2006-04-24
[QUOTE=robglinka]It could be a very simple problem as well, if you unplug the USB drive while it is writing to it, you would corrupt the file it is writing and experience the problems you are having. 

I would suggest waiting until the file completes writing and then unmounting the drive manually before removing it.

-rob[/QUOTE]

I never unplug it while it is in the middle of writing to it. I don't manually unmount it though, but I don't in Windows either and it works fine...

---

### Post by Gavman on 2006-04-24
I have this problem too
```
Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1000      255983+   6  FAT16
Partition 1 has different physical/logical endings:
     phys=(998, 15, 32) logical=(999, 15, 31)

```

but my drive is just a generic usbdisk I bought, and its formatted in FAT32

---

