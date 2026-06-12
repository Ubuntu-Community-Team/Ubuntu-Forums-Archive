---
title: "New USB HDD to ext4"
date: 2012-09-30
forum: General Help
---

### Post by rbscairns on 2012-09-30
I have a new 80GB USB external HDD that I wish to format to ext4 and use with my Ubuntu 12.04 (gnome classic).

I thought "Simple enough. I will just use Gparted that is included with Ubuntu 12.04." So here is what I did:

[LIST=1]
[*]Connected my USB HDD to my PC.
[*]Opened GParted (System Tools>Administration>GParted Partition Editor.
[*]From the drop-down box, I selected my 80GB HDD (/dev/sdc).
[*]Selected Device>Creat Partition Table and [Apply]. This created an MS-DOS partition table.
[*]I then selected the unallocated partition (unallocated file system, 74.53GiB, no flags), right clicked and selected New.
[*]I left everything as default, except changed the File System to ext4, and clicked [Add]. The Disk Label entry was left blank.
[*]I then selected Eddit>Apply All Operations and clicked [Apply].
[*]After a wait, I then get an error message "An error occured while applying the operations".
[/LIST]
Details of this error message are:

> GParted 0.11.0 --enable-libparted-dmraid

Libparted 2.3

Create Primary Partition #1 (ext4, 74.53 GiB) on /dev/sdc  00:00:34    ( ERROR )
    	
create empty partition  00:00:34    ( ERROR )
    	
path: /dev/sdc1
start: 2,048
end: 156,301,311
size: 156,299,264 (74.53 GiB)
libparted messages    ( INFO )
    	
/dev/sdc: unrecognised disk label

Where am I going wrong? How can I format this USB HDD to ext4 so that I can use it with Ubuntu 12.04?

---

### Post by Epodx64 on 2012-09-30
I have similar problems like that with PenDrives he's what I did to resolve it first unmount and remove the drive (I'd always reboot with the drive unplugged) then when Ubuntu loads up plug the drive in and let it automount (i'd assume) then load Gparted let Gparted unmount the drive then instead of formatting it or unallocating it delete the entire partition after that's complete complete then you should be able be able to format it to /ext4 without issue.

---

### Post by OM55 on 2012-09-30
If the hard-drive has bad sectors, GParted may have a problem with that and will not be able to complete the task. If that is the case you will need to do it manually via command line. See the following for help on this: [http://ubuntuforums.org/archive/index.php/t-1244058.html](http://ubuntuforums.org/archive/index.php/t-1244058.html)

Also notice that /dev/sdc is the _entire_ drive, which is (or will be) divided to 1 or more partitions (sdc1, edc2... etc.). Only the partitions can be formated to a specific format, like ext4.

This also can be done this via command line. The syntax is:

```
sudo mkfs.ext4 -L <label_name> <device> 
```or
```
mke2fs -L <label_name> <device>
```for example:

```
sudo mkfs.ext4 -L NewDrive /dev/sdc1
```

---

### Post by rbscairns on 2012-10-01
Looks like it was a faulty HDD or incompatable enclosure.

I purchased another USB external HDD and had no problems partitioning it and formatting it to ext4 using GParted.

The old (faulty?) USB HDD accepts NTFS formatting usind Windows, so I will give that away to a needy student.

---

