---
title: "How do I mount an USB stick"
date: 2011-05-12
forum: General Help
---

### Post by Robbyx on 2011-05-12
I added this entry to fstab:

# kingston memory stick (sdb1)
UUID=E0D0-35DF  /dev/usb-kingston  vfat unmask=0

Previously I created a folder 'usb-kingston'. It is owned by root with read & write for root. The group and other are read only.

When restarting Ubuntu I get an error message reporting a problem mounting memory stick. **What have I done wrong?** Was I right to have created a new folder in dev ? The other devices do not appear to be in folders but in character devices.

---

### Post by TeoBigusGeekus on 2011-05-12
I'd create a folder in /media, but more importantly, you should add 2 zeros in the fstab entry
```
UUID=E0D0-35DF  /dev/usb-kingston  vfat unmask=0 0 0
```

---

### Post by abohsin on 2011-05-12
It is safer to open the /etc/fstab, copy any of the existing lines and edit it according to your parameters.

---

### Post by coffeecat on 2011-05-12
> **Robbyx said:**
> Was I right to have created a new folder in dev ?

No. Leave /dev alone. It's for the system to create device nodes. For /etc/fstab you need to define a mountpoint and use a custom folder in /media as TeoBigusGeekus suggests or in /mnt or a subfolder in /mnt.

Also - it's 'umask=0', not 'unmask=0'.

**EDIT**: You might find this community documentation page useful:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by Robbyx on 2011-05-12
Thank everyone. I now have it working. I moved the device to media as suggested.

---

### Post by Robbyx on 2011-05-12
Under places I am seeing 3 entries for the stick two icons look like disk drives but the third looks like the usb stick. Is there something else i have done wrong? Is it something to do with the defaults it fstab?

---

### Post by Robbyx on 2011-05-12
This is my latest fstab:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4a60ff9d-f704-4d04-a829-4c4702f5c203 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=45a2e92c-c759-4732-9662-988da7f8ea7b /home           ext3    defaults        0       2
# /media/mydocs was on /dev/sdc1 during installation
UUID=724E07853D78E7A8 /media/mydocs   ntfs    defaults,umask=007,gid=46 0       0
# /media/video was on /dev/sda6 during installation
UUID=86290d05-e673-4310-9f3e-93af30cc13af /media/video    reiserfs defaults        0       2
# swap was on /dev/sda4 during installation
UUID=e36cb6cf-f372-4418-bd8b-f36a27dc3e76 none            swap    sw              0       0
# kingston memory stick (sdb1)
UUID=E0D0-35DF  /media/kingston  vfat defaults,umask=000,user  0 0 

Looking at the drives from within the file manager pcmanfm** I am still seeing multiple entries for the stick**. Only one works(usb stick icon) the other drive symbol when clicked on reports:

> mount: /dev/sdb1 already mounted or /media/kingston busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/kingston

---

### Post by coffeecat on 2011-05-13
> **Robbyx said:**
> Looking at the drives from within the file manager pcmanfm** I am still seeing multiple entries for the stick**. Only one works(usb stick icon) the other drive symbol when clicked on reports:

Well - I was wondering why you were using fstab to mount a USB stick at all. Was there a specific reason? Any attached USB devices or other internal partitions will appear in Places - I believe it's udisks that automatically detects them. The one that you click on which gives you the error message I guess would be the udisks-generated one and, of course, errors on you because you can't mount an already-mounted filesystem.

If you didn't have your fstab entry and simply had the USB stick plugged in when you booted up it would be automoatically mounted to a dynamically created mountpoint in /media. Would this not be an option for you? Then you would have just the one entry in Places.

You say you have three entries in Places. How many partitions do you have on the stick? Post the output of:

```
sudo fdisk -lu
```

---

### Post by Robbyx on 2011-05-13
> **coffeecat said:**
> Well - I was wondering why you were using fstab to mount a USB stick at all. Was there a specific reason? 
If you didn't have your fstab entry and simply had the USB stick plugged in when you booted up it would be automoatically mounted to a dynamically created mountpoint in /media. Would this not be an option for you? Then you would have just the one entry in Places.

```
sudo fdisk -lu
```

> robin@robin-EP35-DS3L:~$ sudo fdisk -lu
[sudo] password for robin: 

Disk /dev/sda: 500.1 GB, 500106780160 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976771055 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00011035

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    59842124    29921031   83  Linux
/dev/sda2        59842125   122849054    31503465   83  Linux
/dev/sda3       122849116   964815704   420983294+   5  Extended
/dev/sda4       964815705   976768064     5976180   82  Linux swap / Solaris
/dev/sda5       122849118   337364999   107257941   83  Linux
/dev/sda6       337365063   964815704   313725321   83  Linux

Disk /dev/sdb: 2055 MB, 2055208960 bytes
16 heads, 32 sectors/track, 7840 cylinders, total 4014080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3aa5e04

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              32     4014079     2007024    c  W95 FAT32 (LBA)

Disk /dev/sdc: 250.1 GB, 250058301440 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488395120 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00075fd0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001   fd  Linux RAID autodetect
robin@robin-EP35-DS3L:~$ 



The reasons for using fstab were:

I had great problems with the auto load. It defaulted to root being the owner. I was not able to easily transfer or delete files on the mem stick.

The auto load was not consistent. The mem stick would be in the usb but would not be read without a reboot. This not withstanding the auto load options in nautilus being switched on. 

Loading via fstab enabled me to control the load options, owners etc.

---

### Post by coffeecat on 2011-05-13
> **Robbyx said:**
> I had great problems with the auto load. It defaulted to root being the owner. I was not able to easily transfer or delete files on the mem stick.

This sounds familiar. Did you, by chance, install the package usbmount? If you did, uninstall it and all your usb problems will melt away and you will be able to automount your USB stick.

---

### Post by Robbyx on 2011-05-13
> **coffeecat said:**
> This sounds familiar. Did you, by chance, install the package usbmount? If you did, uninstall it and all your usb problems will melt away and you will be able to automount your USB stick.

Upon your advice, for which I thank you, I have removed usbmount and things are much better. Indeed I hope all my usb problems have just turned to slush.

---

### Post by coffeecat on 2011-05-13
I'm glad to hear it. :)

Fortunately, I'd come across this before. The app usbmount is not designed to be used with a GUI desktop - I presume it's meant for server installs - and causes conflicts with the built-in GUI way of automounting USb drives. It was the root-only access to a FAT32-formatted drive that was the clue.

Good luck!

---

