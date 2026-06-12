---
title: "Grub Problem"
date: 2006-04-08
forum: General Help
---

### Post by somedaysoon on 2006-04-08
I have a problem with Grub.

First let me tell you my hard drive setup.
Primary Master - Windows XP
Primary Slave - NTFS
Secondary Master - Ubuntu
Secondary Slave - DVD

I installed Grub to /dev/hdc1 which is /boot

Then I set the first boot device to the Secondary Master drive and Grub loaded but I got an Error 17.

I played around with it for awhile and I finally got Ubuntu to load. Grub had root (hd2,0) which should be right, but it wasn't working. When I changed it to root (hd0,0) Ubuntu loads. Shouldn't that load XP?

I went into device manager in Ubuntu after I got it to boot and my Primary Master had an ide.channel of 0(0x0) and my Secondary Master also had an ide.channel of 0(0x0).

I can't get Grub to boot XP at all. In order to boot XP I have to change the boot order of the drive in the BIOS so the XP drive boots first.

Please help because I think something was installed wrong.

---

### Post by somedaysoon on 2006-04-09
No help?

---

### Post by NiN on 2006-04-09
If you set the boot disk in bios, it also alters the drive numbering of grub.
if you want to boot from the second disk, keep in mind that it will be seen as hd0 by grub.
if you want to boot windows with this setting, you have to add
```

map (hd0) (hd1)
map (hd1) (hd0)

```
to the windows boot entry in grub (just add it after the title section).
This will change the drive numbering back to  the original order (as seen by windows)

---

### Post by somedaysoon on 2006-04-09
I added it before the root (hd0,0) command and it didn't work.

```
map (hd0) (hd1)
map (hd1) (hd0)
root (hd0,0)
savedefault
i forgot what was here but not this
boot
```


I don't think grub recognizes the Windows drive at all. If I go into command line and type in root (hd1,0) it says something like file system not found. Shouldn't it find an NTFS file system?  I have also tried other drives (hd2,0) etc. It just doesn't see the Primary Master nor Primary Slave drives.

Let me see if I got this straight....

I install Grub onto my Secondary Master. I have to change the bios to boot my Secondary Master in order to load Grub. Grub views the drive that it is on as (hd0) even though it is (hd2). I have a problem.


I think that is stupid. If that is how it is setup then Grub can't multiboot systems unless it is on the Primary Master.

---

### Post by Sutekh on 2006-04-09
If you boot up Ubuntu, can you provide the output from
```
sudo fdisk -l
```
 - this lists all the partitions on your discs, then we will know what is where

```
cat /boot/grub/device.map
```
 - this will print the file - device.map to the screen.  The device.map is what GRUB uses to map device locations (/dev/hda1 for example) to the terminology GRUB uses (hd0).

 - an example file (mine) would be
```
(hd0)   /dev/hda
(hd1)   /dev/sda
(hd2)   /dev/sdb
```

With these two bits of information we can work out what partition Windows is on and where GRUB maps it.  Then we can change the menu entry to boot Windows.

---

### Post by somedaysoon on 2006-04-09
Ok, first let me just thank you for taking the time to help me out. I really appreciate it.


The output of the commands:

```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3473    27896841    7  HPFS/NTFS
/dev/hda2            3474        7297    30716280    f  W95 Ext'd (LBA)
/dev/hda5            3474        7297    30716248+   7  HPFS/NTFS

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1          10       80293+  83  Linux
/dev/hdc2              11         536     4225095   83  Linux
/dev/hdc3             537        1059     4200997+  83  Linux
/dev/hdc4            1060        2434    11044687+   5  Extended
/dev/hdc5            1060        1582     4200966   83  Linux
/dev/hdc6            1583        1977     3172806   83  Linux
/dev/hdc7            1978        2238     2096451   83  Linux
/dev/hdc8            2239        2289      409626   83  Linux
/dev/hdc9            2290        2327      305203+  83  Linux
/dev/hdc10           2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sda: 522 MB, 522043904 bytes
16 heads, 63 sectors/track, 1011 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1010      509008+   6  FAT16
```

```
(hd0)    /dev/hda
(hd1)    /dev/hdb
(hd2)    /dev/hdc
(hd3)    /dev/sda
```

The sda1 is my usb/thumb drive.

---

### Post by Sutekh on 2006-04-09
Which partition is Windows on?  /dev/hda1 or /dev/hdb1 or both?

I should have asked you to post your menu.lst too.

```
cat /boot/grub/menu.lst
```

Anyway, you should back the menu up before editing it
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
sudo gedit /boot/grub/menu.lst
```

To boot Windows on /dev/hda1 use this entry
```
title		Microsoft Windows XP
root		(hd0,0)
savedefault
chainloader	+1
```
To boot Windows on /dev/hdb1 use this entry
```
title		Microsoft Windows XP
root		(hd1,0)
savedefault
[b]map		(hd0) (hd1)
map		(hd1) (hd0)[/b]
chainloader	+1
```
The entry for booting Windows on /dev/hdb1 is different because Windows like to be on the first partition of the first drive.  The map commands fool Windows into thinking this.

The Ubuntu boot option should look *something* like this
```
title Ubuntu, kernel 2.6.12-9-386
root (hd2,0)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot
```

---

### Post by somedaysoon on 2006-04-10
This is my problem because what you are saying should work but it doesn't.


hda1 is my Windows partition, there is also a logical ntfs partition on this same drive. This is hda5.

hdb1 is just an storage drive formatted with NTFS.



This does not boot ubuntu
```

title Ubuntu, kernel 2.6.12-9-386
root (hd2,0)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot
```




This boots ubuntu
```
title Ubuntu, kernel 2.6.12-9-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot
```


This does not boot windows
```
title		Microsoft Windows XP
root		(hd0,0)
savedefault
chainloader	+1
```

I can't get it to boot windows. The problem is that Grub thinks Ubuntu is on hd0 when it should really be on hd2. I have tried finding which drive Grub thinks is the Windows drive but I can't find it. The only recognizable drive is the linux drive and that is hd0 (according to grub).

---

### Post by Sutekh on 2006-04-10
I think I understand what you are saying now, and it sounds really strange.

Ok so try going into the GRUB command prompt, press 'c' at the menu and type
```
hd<TAB>
```as in type 'hd' then press TAB.  What are your available options?  Does it list hd0, hd1, hd2, etc?


Also you can edit the GRUB menu from the GRUB menu, saving you the time of rebooting and loading Ubuntu etc.

If you select the Windows entry you can edit it with 'e' and then edit the root    (hd0,0) line.  Try changing it to (including the map commands)
```
title		Microsoft Windows XP
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
If that doesn't work, you should be sent back to the GRUB menu and you could try changing it again, but instead of hd1 use hd2, etc.

---

### Post by somedaysoon on 2006-04-10
Typing in hd and then pressing tab did not return any results.

I have tried other drives. I mentioned earlier that I have already tried this.


Do you think I should reinstall Grub? If so, how hard is it? What do I need to do?

---

### Post by petri on 2006-04-13
Yes you can try reinstall grub if you haven't already done that.
There is a guid [howto]("http://ubuntuforums.org/showthread.php?t=76652&highlight=howto+install+grub") do it.

And [here]("http://www.gnu.org/software/grub/manual/grub.html#Stage1-errors")    you will find what those grub error codes really want to say.

---

