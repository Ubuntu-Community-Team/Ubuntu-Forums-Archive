---
title: "Nautilus does not display space taken up by SD card"
date: 2010-08-22
forum: General Help
---

### Post by altonbr on 2010-08-22
I have a miniSD card that I use for my BlackBerry. It's 8GB large so I decided to put it in an SD jacket and use it in my camera.

When I plug the SD card into my computer, Nautilus and Disk Usage Analyzer show 1.4 GB yet `fdisk -l`, `df -h` and gparted all show 2.8GB being used.

```
$ sudo fdisk -l
{snip}
Disk /dev/mmcblk0: 7969 MB, 7969177600 bytes
221 heads, 20 sectors/track, 3521 cylinders
Units = cylinders of 4420 * 512 = 2263040 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               2        3522     7778304    b  W95 FAT32
```
```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
{snip}
/dev/mmcblk0p1        7.5G  2.8G  4.7G  37% /media/BlackBerry
```

The files shown on the disk are only 1.4GB and my BlackBerry files, yet when I put the disk into my camera, I can see the unaccounted for photos and videos.

I've used gparted to see if there was some unknown/invisible-to-nautilus partition and I can't find one (just as `df -h` says).

I tried doing a `dd` of the entire disk, but that does me no good when I mount the image... it still shows me 1.4GB.

What can I do to see the other files? I'm a computer science undergrad, so you can be as technical as you wish.

---

### Post by altonbr on 2010-08-22
I'm adding a screenshot of Nautilus' examination of /media/BlackBerry (2.7 GB) and /media/BlackBerry/BlackBerry/ (1.4 GB).

---

### Post by altonbr on 2010-08-23
Lastly, I installed a great CLI program called 'testdisk' and ran one of its programs called 'photorec'. The program was able to find files within my entire 8GB disk, searching the empty space and found all current files on the disk, including some previously "deleted" files.

However, the files come out with obscure file names and are out of order for my purposes.

So the search continues.

---

### Post by altonbr on 2010-08-23
Nautilus/gthumb crashes when I try and retrieve the photos of my camera.

Anyone?

---

