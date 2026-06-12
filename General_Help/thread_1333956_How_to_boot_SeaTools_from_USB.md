---
title: "How to boot SeaTools from USB??"
date: 2009-11-21
forum: General Help
---

### Post by Devi 710 on 2009-11-21
Does any one know how to make the ISO image for Seagate's Seatools boot from a USB?

SeaTools is a special hard drive diagnostics and repair program I need to fix my netbooks hard drive (so I have no CD Drive to boot from). Info here:
[http://www.seagate.com/www/en-us/support/downloads/seatools](http://www.seagate.com/www/en-us/support/downloads/seatools)
-the "SeaTools for DOS" is the one that works with Linux

I have tried Unetbootin, a grub screen will appear with 'default' as the only option which doesn't boot anyting.

The 'USB Startup Disk Creator' in Ubuntu won't accept the ISO file.

I've tried to mount the ISO in a Virtual Drive and copy the files, but the USB isn't bootable.

I would really love if someone could get this working. 

Thank you,

Devi

---

### Post by MestreLion on 2010-10-30
Same problem here... Ive tried dozens of possible solutions, from the friendly Unetbootin to the extreme DD the iso (to partition and to device). Had several diferent results depending on what i did, but none actually worked.

Im still researching and trying, but ANY help would be appreciated

---

### Post by gmargo on 2010-10-30
I managed to run the SeaTools tool from a USB stick.

First off, I already had a bootable FreeDOS USB stick that I made a few months back in order to burn a new bios on a laptop. (This step left as an exercise for the reader :-)

To get the SeaTools executable out of the provided .ISO, do the following:
```

$ sudo mkdir /media/disk1 /media/disk2
$ sudo mount -t iso9660 -o ro,loop SeaToolsDOS222ALL.576.ISO /media/disk1
$ sudo mount -t vfat -o ro,loop /media/disk1/SeaTools.ima /media/disk2

```The file you want is /media/disk2/seatools.zip.  Unzip the contents of that file into a directory on a FreeDOS USB stick.  Boot the FreeDOS stick, navigate to the directory with the unzipped files, then run the "seatools.exe" executable.  For me it ran fine and found my two seagate drives, however I did not run any other tests.

---

### Post by morrie on 2011-04-24
hehe....get a usb floppy drive!  Then it will boot from USB.:)

Trust me, I speak from experience, this is not easy to do.  I finally gave up and used a usb floppy drive to get the job done (hated the idea so much I wasted 4 hours trying to boot usb dos with Seatools.  I did hear that Universal boot disk includes seatools (which is weird)...

---

### Post by mspacek on 2011-06-30
Here's a little guide I found to do just this. It's tailored for Fedora though:

[http://fetzig.org/2010/07/12/preparing-a-bootable-seatools-usb-drive-in-fedora/](http://fetzig.org/2010/07/12/preparing-a-bootable-seatools-usb-drive-in-fedora/)

I modified it to work with ubuntu (maverick in my case, but that shouldn't matter). Here's my recipe:

1. install syslinux:
```
$ sudo apt-get install syslinux
```

2. repartition and format usb (/dev/sdb in my case) as FAT (use disk utility in admin menu)
    - I named it "SEATOOLS"

3. mark as bootable (use gparted)

4. copy syslinux master boot record to drive:
```
$ sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sdb
```

5. install syslinux on the drive partition:
```
$ sudo syslinux /dev/sdb1
```

6. mount drive (use nautilus)

7. copy the MEMDISK bootloader from /usr/share/syslinux/memdisk to drive:
```
$ cp /usr/lib/syslinux/memdisk /media/SEATOOLS
```

8. copy the SeaTools .iso to drive

9. create a file named 'syslinux.cfg' on the drive, with this in it (use correct .iso name):

```

DEFAULT SeaTools
LABEL SeaTools
  LINUX memdisk
  INITRD SeaToolsDOS220EURO.144.ISO
  APPEND iso

```

10. you're done. Try booting with it. Here's what my usb stick looks like at the end of all of this:

```

$ ls -al
total 3136
drwx------ 2 username username    4096 2011-06-30 13:44 .
drwxr-xr-x 3 root     root        4096 2011-06-30 13:39 ..
-r--r--r-- 1 username username   32768 2011-06-30 13:34 ldlinux.sys
-rw-r--r-- 1 username username   25244 2011-06-30 13:41 memdisk
-rw-r--r-- 1 username username 3137536 2011-06-30 10:52 SeaToolsDOS220EURO.144.ISO
-rw-r--r-- 1 username username      97 2011-06-30 13:44 syslinux.cfg

```

---

### Post by kolinab on 2012-04-09
The lovely thing about these instructions is that as far as I can see it can be adapted for nearly any .iso. 

I'm looking forward to trying this later with a different .iso utility I need to run. Thanks for posting these instructions!

---

### Post by oldos2er on 2012-04-10
Closed, necromancy.

---

