---
title: "Auto mounting HDD at boot"
date: 2010-02-21
forum: General Help
---

### Post by jesseAnger on 2010-02-21
[B]I have a 500 GB ext4 formatted HHD which i have to manualy mount when ubuntu starts. I have read much on the topic but am still unsure what i should add to fstab

_my output when entering "sudo fdisk -l" is[/B]_

[FONT="Courier New"]"Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005cf80

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       28571   229496526   83  Linux
/dev/sda2           28572       28696     1004062+   5  Extended
/dev/sda3           28697      121601   746259412+  83  Linux
/dev/sda5           28572       28696     1004031   82  Linux swap / Solaris

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bde6bde

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30401   244196001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00099623

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x58550da3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      310101   156290872+   c  W95 FAT32 (LB"[/FONT]

**_Here is the output when $ cat /etc/fstab is entered_**

[FONT="Courier New"]"jesse@hub:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a9490a0a-c17c-4223-b51f-9d369b3faa54 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0f9e52de-4db3-42a6-844e-8c82e5430c32 none            swap    sw              0       0
# swap was on /dev/sdc1 during installation
UUID=b750427d-0788-47e6-a33b-4ccbe826a241 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0"[/FONT]

[B]My question is what should my additions to the fstab file be to have the 500 GB auto mount?
[/B]

---

### Post by Barriehie on 2010-02-21
From the terminal (Applications > Accessories > Terminal) make a mount point:
```

cd /media
sudo mkdir reallybigdrive (or whatever)
gksudo gedit /etc/fstab

```
At the end of the file:
```

/dev/sdb1  /media/reallybigdrive  auto  auto,user,exec,rw  0  2

```

This last line will mount on /media/reallybigdrive directory, auto-detect the filysystem type, auto-mount at bootup, users can mount the device, execute files, mount as read/write. The 0 tells dump not to worry about backing it up and the 2 tells fsck to scan.

After you've saved /etc/fstab do this in a terminal:
```

mount -a

```
It should mount the drive, at the next reboot/restart it should automount.

---

### Post by jesseAnger on 2010-02-21
That worked wonderfully, thank you for your help.

---

### Post by Barriehie on 2010-02-21
> **jesseAnger said:**
> That worked wonderfully, thank you for your help.

Anytime!

---

### Post by inspiredminds on 2010-04-03
Thanks barriehie !! that worked for me too.

---

### Post by dgaud on 2010-04-28
I had the same problem, but with a different twist. I added the mount point to the fstab file as:

```
/media/Rama II etc...
```

but you see my partition name has a space in it, so everytime I ran sudo mount -a, it would prompt an error in the fstab file. The directory created in the media folder shows as "/media/Rama\ II" which is also strange. Anyway, I created a new mount point w/o the space, i.e. "RamaII" and is working now...

Is there any special format for these cases with spaces or special characters in the partition name?

Thanks!

---

### Post by rnerwein on 2010-04-28
hi
uninx/linux don't like spaces in any name.
but try:[COLOR=Red] "[/COLOR]Rama II ...[COLOR=Red]"[/COLOR]    --> qoute it.
but in my opinion -> don't use /media just create your mount point in /   ( /my_mountpoint ) and even it would be nice to
include the filesystem type.

/dev/sdXY   [COLOR=Black]/[COLOR=Red]"[COLOR=Black]Rama II .. [COLOR=Red]"   ext4 defaults [COLOR=Black]0 2

the option [COLOR=Blue]defaults[/COLOR] include the most options you need ( see man mount )
ciao


[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

---

### Post by dgaud on 2010-04-28
> **rnerwein said:**
> hi
uninx/linux don't like spaces in any name.
but try:[COLOR=Red] "[/COLOR]Rama II ...[COLOR=Red]"[/COLOR]    --> qoute it.
but in my opinion -> don't use /media just create your mount point in /   ( /my_mountpoint ) and even it would be nice to
include the filesystem type.

/dev/sdXY   [COLOR=Black]/[COLOR=Red]"[COLOR=Black]Rama II .. [COLOR=Red]"   ext4 defaults [COLOR=Black]0 2

the option [COLOR=Blue]defaults[/COLOR] include the most options you need ( see man mount )
ciao


[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]

Hello. Thanks for the quick reply, but it still doesn't work with the space. Here is what I tried:

```
/dev/sdb1 /media/"Rama II" ntfs defaults 0 2
```

I have another ntfs partition that loads as:

```
/dev/sda4 /media/Rama ntfs umask=222,utf8 0 0
```

EDIT: I discovered a few things reading the manual for fstab (man fstab):
1. The order of the mount process is important. I had my cd-rom (/dev/sdc1) loading before my usb drive (/dev/sdb1)
2. The spaces in the fstab file are used to delimit fields, so I don't see a way to implement them for partition names.
3. I commented the line for the usb drive in the fstab file and Ubuntu is loading it by itself automatically, although read-only, but it works!

---

