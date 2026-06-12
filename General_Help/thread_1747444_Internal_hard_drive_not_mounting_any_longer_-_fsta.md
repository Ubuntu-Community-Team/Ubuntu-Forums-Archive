---
title: "Internal hard drive not mounting any longer - fstab?"
date: 2011-05-02
forum: General Help
---

### Post by winchendonsprings on 2011-05-02
Awhile back I added a line at the bottom of my /etc/ftsab to auto mount a drive at boot. It didn't work and I deleted the line. Well I think I only deleted the single line. Anyway the drive used to mount no problem via nautilus, Now it doesn't.

Errors

```
$ sudo mount /dev/sda /media/openSpaceI 
```gives this error

```
mount: wrong fs type, bad option, bad superblock on /dev/sda,        missing codepage or helper program, or other error        In some cases useful info is found in syslog - try        dmesg | tail  or so 
```gives this
```

$ dmesg | tail [ 9344.234380] compiz[6098]: segfault at 28 ip 00007f1fa0641335 sp 00007fff0b306700 error 4 in libregex.so[7f1fa063c000+8000] [ 9987.879043] nautilus[6899]: segfault at 1505b817b60f ip 00007ff6eeefdb8d sp 00007fff09aa6170 error 4 in libgobject-2.0.so.0.2800.6[7ff6eeeca000+4e000] [10001.231835] compiz[7360]: segfault at 28 ip 00007f38e0cfe335 sp 00007fff3228d380 error 4 in libregex.so[7f38e0cf9000+8000] [10113.817592] compiz[7429]: segfault at 28 ip 00007f01c11cd335 sp 00007fffac4f4250 error 4 in libregex.so[7f01c11c8000+8000] [10116.592022] compiz[7651]: segfault at 28 ip 00007f4369548335 sp 00007fffb3b2b030 error 4 in libregex.so[7f4369543000+8000] [10117.958485] compiz[7666]: segfault at 28 ip 00007f3861d7d335 sp 00007fff268395d0 error 4 in libregex.so[7f3861d78000+8000] [10366.207793] EXT4-fs (sda): bad geometry: block count 156282966 exceeds size of device (156282701 blocks) [10855.975855] EXT4-fs (sdb): mounted filesystem with ordered data mode. Opts: (null) [10863.666747] EXT4-fs (sda): bad geometry: block count 156282966 exceeds size of device (156282701 blocks) [11125.922998] EXT4-fs (sda): bad geometry: block count 156282966 exceeds size of device (156282701 blocks)
```Any ideas?
gui error - [http://dl.dropbox.com/u/545099/error1.png](http://dl.dropbox.com/u/545099/error1.png)

my fstab - [http://dl.dropbox.com/u/545099/fstaberror1.png](http://dl.dropbox.com/u/545099/fstaberror1.png)

side note - also is it impossible to get rid of this  greased lightbox ?
> 


<img id="greasedLightboxImage">


[Greased Lightbox]("http://shiftingpixel.com/lightbox/")&#8594;&#8592;+-&#8635;

Loading image
Click anywhere to cancel

Image unavailable


<img id="greasedLightboxPreload"><img id="greasedLightboxPrefetch"><img id="greasedLightboxImage">


[Greased Lightbox]("http://shiftingpixel.com/lightbox/")&#8594;&#8592;+-&#8635;

Loading image
Click anywhere to cancel

Image unavailable


<img id="greasedLightboxPreload"><img id="greasedLightboxPrefetch"><img id="greasedLightboxImage">


[Greased Lightbox]("http://shiftingpixel.com/lightbox/")&#8594;&#8592;+-&#8635;

Loading image
Click anywhere to cancel

Image unavailable


<img id="greasedLightboxPreload"><img id="greasedLightboxPrefetch">

---

### Post by TeoBigusGeekus on 2011-05-02
Is this an ntfs drive?

---

### Post by winchendonsprings on 2011-05-02
No, ext4

---

### Post by TeoBigusGeekus on 2011-05-02
Wait a minute...
When mounting, you have to specify the partition you want to mount, not the whole drive - even if the drive has only one partition.
So the correct command would be 
```
sudo mount /dev/sda1 /media/openSpaceI
```
Replace 1 with whatever applicable.

---

### Post by winchendonsprings on 2011-05-02
See screen shot - [IMG]http://dl.dropbox.com/u/545099/fdisk.png[/IMG]

The drive in question is the 640gb  /dev/sda I believe.  Because it is not the 320gb drive nor the 640gb boot drive.

---

### Post by TeoBigusGeekus on 2011-05-02
Is it empty/unformatted? 
fdisk doesn't see any partitions.
Try to fsck the drive
```
sudo fsck /dev/sda
```
to check it for errors.

---

### Post by winchendonsprings on 2011-05-02
The drive is ext4 formatted and full of videos, backed up apps, music, etc. It worked fine 3 days ago.

I could hear the drive spin up when I ran 
```

sudo fsck /dev/sda
```results -
```

ry@ry-EX58-UD5:~$ sudo fsck /dev/sda
[sudo] password for ry: 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
The filesystem size (according to the superblock) is 156282966 blocks
The physical size of the device is 156282701 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? 
```

---

### Post by winchendonsprings on 2011-05-02
What do you think of this method?

[http://ubuntuforums.org/showpost.php?p=9485779&postcount=7](http://ubuntuforums.org/showpost.php?p=9485779&postcount=7)
> 
On to repairing. Creating backup of partition table with sfdisk:
 	Code:
 	sfdisk -d /dev/sda > PT.txt 


that will try to backup 640gb? I have nowhere to back that much up to.

---

### Post by winchendonsprings on 2011-05-03
So I ran the extended version of self check in disk utility and it was ok and healthy. 
Screenshots-
[IMG]http://dl.dropbox.com/u/545099/selftest.png[/IMG][IMG]http://dl.dropbox.com/u/545099/diskutility.png[/IMG]

Anyone have a clue how to fix this - 
[IMG]http://dl.dropbox.com/u/545099/error1.png[/IMG]

I still think it has something to do with me editing the fstab file, no?

---

