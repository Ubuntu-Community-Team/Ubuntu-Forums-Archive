---
title: "Only one thing holding me to windows now"
date: 2006-06-30
forum: General Help
---

### Post by Drifter on 2006-06-30
I am unable to use cd recorder and dvd recorder.  The drives will see what is in them but I can't record anything to them.  Also if I put a cdrw disk in and try to erase it, it gives an error message . I have been working on this problem myselve and reading posts and howto's but have not figured anything out yet.  Does anyone know what could be the problem.

---

### Post by user1397 on 2006-06-30
[quote=Drifter]I am unable to use cd recorder and dvd recorder.  The drives will see what is in them but I can't record anything to them.  Also if I put a cdrw disk in and try to erase it, it gives an error message . I have been working on this problem myselve and reading posts and howto's but have not figured anything out yet.  Does anyone know what could be the problem.[/quote]do you use nautilus to burn cd's and dvd's or a special program like gnomebaker or k3b?

---

### Post by Drifter on 2006-06-30
I use gnomebaker and k3b, I don't know how to use nautilus.

---

### Post by user1397 on 2006-06-30
using nautilus is easy.  you go to the file you want to burn, right-click on it, and click **write to disc**.

so what's the problem when you use k3b (as i'm most familiar with k3b)?  you can't burn **any  **file?  what are some example error messages?

---

### Post by Drifter on 2006-06-30
I can burn somethings with k3b, but if I use a cdrwdisk it will not erase it.  The message is this:  The Erasing process failed. Do you want to see the debugging output?

Debugging: 

System
-----------------------
K3b Version: 0.12.14

KDE Version: 3.5.2
QT Version:  3.3.6
Kernel:      2.6.15-25-386
Devices
-----------------------
JLMS XJ-HD166S DS1A (/dev/hdc, ) at /media/cdrom0 [CD-ROM; DVD-ROM] [DVD-ROM; CD-ROM] [None]

ATAPI CD-RW 16/12/40X 110C (/dev/hdd, ) at  [CD-R; CD-RW; CD-ROM] [CD-ROM; CD-R; CD-RW] [SAO; TAO; RAW; SAO/R96P; SAO/R96R; RAW/R16; RAW/R96R]
Used versions
-----------------------
cdrecord: 2.1.1a01

cdrecord command:
-----------------------
/usr/bin/X11/cdrecord.mmap -v gracetime=2 dev=/dev/hdd speed=12 -tao driveropts=burnfree -eject blank=fast -force 

cdrecord
-----------------------
/usr/bin/X11/cdrecord: Warning: Running on Linux-2.6.15-25-386

/usr/bin/X11/cdrecord: There are unsettled issues with Linux-2.5 and newer.
/usr/bin/X11/cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/hdd'
devname: '/dev/hdd'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Error trying to open /dev/hdd exclusively (Device or resource busy)... retrying in 1 second.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.
TOC Type: 1 = CD-ROM
/usr/bin/X11/cdrecord: Device or resource busy. Cannot open '/dev/hdd'. Cannot open SCSI driver.
/usr/bin/X11/cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
/usr/bin/X11/cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
/usr/bin/X11/cdrecord: 
/usr/bin/X11/cdrecord: For more information, install the cdrtools-doc
/usr/bin/X11/cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .

---

### Post by user1397 on 2006-06-30
have you tried erasing a cdrw just by deleting its data in the file browser (nautilus)?

---

### Post by Drifter on 2006-06-30
No I have not tried that how do u get to nautilus, where is it.

---

### Post by yopnono on 2006-06-30
Check your permission on the dev/hdd, if it's root only
try this from terminal
```
sudo chown root:cdrom /dev/hdd
```
If that work to burn cd/dvd then put this in the rc.local file found in /etc (before the "exit 0" in the file)
```
chown root:cdrom /dev/hdd
```
And reboot the machine and try again.

---

### Post by user1397 on 2006-06-30
nautilus is in applications > accesories > file browser

---

### Post by Drifter on 2006-06-30
I do not have a file browser in applications, accessories.

---

### Post by woedend on 2006-06-30
places -> home folder
will get you into nautilus

but the problem you are having is that it seems like your CD is mounted when it shouldn't be(ie why it's not locking).
unmount/remove any cds from computer.
Lets try this and see what happens for now -
system->preferences->removable drives and media
remember which boxes are checked here(write down perhaps) under the Storage tab, then uncheck all pertaining to CDs or removable media(or to be easy, uncheck everything for now).

try burning again and see if same error message arises.
let me know if this does not work.

---

