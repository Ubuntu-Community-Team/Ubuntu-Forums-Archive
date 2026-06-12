---
title: "Mount USB Flash drive"
date: 2006-03-26
forum: General Help
---

### Post by PowerWCRulez on 2006-03-26
Hello, I tried to mound USB 64MB flash drive on sdd1, but it's says need get root access to mount it, I tried to enter the password, that says auth failed :( How I can mounting the USB flash drive on my Live CD?

---

### Post by melissawm on 2006-03-26
If you type on a terminal something like 

> sudo mount /dev/sdd1 /media/usbdisk

it will prompt you for your user password (not the root pwd). Does that work? (where /media/usbdisk is the directory where you want to mount your flash drive)

---

### Post by PowerWCRulez on 2006-03-26
[QUOTE=melissawm]If you type on a terminal something like 



it will prompt you for your user password (not the root pwd). Does that work? (where /media/usbdisk is the directory where you want to mount your flash drive)[/QUOTE]

Okay I got the message that says:

warty@ubuntu:~ $ sudo mount /dev/sdc1 /media/usbdisk
mount: mount point /media/usbdisk does not exist

I run a dmesg listing shows..

usb 2-1.1: new full speed USB device using address 9
scsi8 : SCSI emulation for USB Mass Storage devices
  Vendor: Flash/SM  Model: Super Talent 2.0  Rev: 2040
  Type:   Direct-Access                      ANSI SCSI revision: 02
SCSI device sdc: 125952 512-byte hdwr sectors (64 MB)
sdc: assuming Write Enabled
sdc: assuming drive cache: write through
 sdc: sdc1
Attached scsi removable disk sdc at scsi8, channel 0, id 0, lun 0
USB Mass Storage device found at 9

I had the files in the flashdrive, how I need to delete the old file?

---

### Post by Sutekh on 2006-03-26
Try creating the ount folder before using the mount command
```
sudo mkdir /media/usbdisk
sudo mount /dev/sdd1 /media/usbdisk
```

What format is the USB disc?  Also is you are running the LiveCD you shouldn't need to enter any password in.  You still need to use sudo with those commands though.

---

### Post by PowerWCRulez on 2006-03-26
[QUOTE=Sutekh]Try creating the ount folder before using the mount command
```
sudo mkdir /media/usbdisk
sudo mount /dev/sdd1 /media/usbdisk
```

What format is the USB disc?  Also is you are running the LiveCD you shouldn't need to enter any password in.  You still need to use sudo with those commands though.[/QUOTE]


Whoa! It's work :) , now how to delete the window program files (XP's) and format it? My usb flash disk is now "usbfdisk" on desktop as USB Flash Disk

---

### Post by Sutekh on 2006-03-26
[QUOTE=PowerWCRulez]Whoa! It's work :) , now how to delete the window program files (XP's) and format it? My usb flash disk is now "usbfdisk" on desktop as USB Flash Disk[/QUOTE]
Good stuff!!

Now.... you want to completely remove Windows XP and format it. 

What do you plan to do with the newly formatted partition?

Is Windows XP on the same hard drive as Ubuntu or a different one?


Also you never said the format of the USB disc.  I just wanted to know as there are some other things you should know about mounting devices of certain filesystems.  Just to ensure it works properly for you.

_

---

### Post by PowerWCRulez on 2006-03-26
[QUOTE=Sutekh]Good stuff!!

Now.... you want to completely remove Windows XP and format it. 

What do you plan to do with the newly formatted partition?

Is Windows XP on the same hard drive as Ubuntu or a different one?


Also you never said the format of the USB disc.  I just wanted to know as there are some other things you should know about mounting devices of certain filesystems.  Just to ensure it works properly for you.

_[/QUOTE]

No hard drive on my lappy (see sigs below), I am running the Live CD, mounted to the USB flash drive (64MB) need to remove the junk files or format on my flash drive (usually it's a game program and text files).

---

### Post by Sutekh on 2006-03-26
Okay I understand now. 

If you want to be able to remove the files, I need to know what the format of the USB disc is. 

If you want to format the USB disc completely, then install parted
```
sudo apt-get install parted
```
You can get some information on its use here - [GNU.org - Parted](http://www.gnu.org/software/parted/)

Or you can download and burn the [GParted LiveCD](http://gparted.sourceforge.net/livecd.php).  It's only 30MB and has a nice interface.

---

### Post by PowerWCRulez on 2006-03-26
[QUOTE=Sutekh]Okay I understand now. 

If you want to be able to remove the files, I need to know what the format of the USB disc is. 

If you want to format the USB disc completely, then install parted
```
sudo apt-get install parted
```
You can get some information on its use here - [GNU.org - Parted](http://www.gnu.org/software/parted/)

Or you can download and burn the [GParted LiveCD](http://gparted.sourceforge.net/livecd.php).  It's only 30MB and has a nice interface.[/QUOTE]

Hello, the parted already on Live CD, and I tried use parted command it's says:

warty@ubuntu:~ $ parted
Error: No device found

and the filesystem list are:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc1                62697      4496     58201   8% /media/usbfdisk

How I can find the format titles (VFat or 32 or whatever) to see it?

---

### Post by Sutekh on 2006-03-26
Ok to use parted (I only just read this too) you can use these commands

Go here for the manual 

[GNU Parted User Manual](http://www.gnu.org/software/parted/manual/html_mono/parted.html)

 - To start parted
```
parted /dev/sdc1
```

 - To remove the old partition, sdc1
```
(parted) rm 1
```

 - To create a new partition, sdc1, FAT32
```
(parted) mkfs 1 fat32
```

 - To check the partition table
```
(parted) print
```

[quote=PowerWCRulez]How I can find the format titles (VFat or 32 or whatever) to see it?[/quote]I don't knw what you mean by this.

---

### Post by PowerWCRulez on 2006-03-26
[QUOTE=Sutekh]Ok to use parted (I only just read this too) you can use these commands

Go here for the manual 

[GNU Parted User Manual](http://www.gnu.org/software/parted/manual/html_mono/parted.html)

 - To start parted
```
parted /dev/sdc1
```

 - To remove the old partition, sdc1
```
(parted) rm 1
```

 - To create a new partition, sdc1, FAT32
```
(parted) mkfs 1 fat32
```

 - To check the partition table
```
(parted) print
```

I don't knw what you mean by this.[/QUOTE]

I found it, here is..

warty@ubuntu:~ $ sudo fdisk -l

Disk /dev/sdc: 64 MB, 64487424 bytes
17 heads, 32 sectors/track, 231 cylinders
Units = cylinders of 544 * 512 = 278528 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         232       62959+   4  FAT16 <32M
Partition 1 has different physical/logical endings:
     phys=(249, 16, 32) logical=(231, 8, 31)

the file system is FAT16, Should I go ahead use a parted command to erase the usb flash drive?

---

### Post by Sutekh on 2006-03-26
[QUOTE=PowerWCRulez]
the file system is FAT16, Should I go ahead use a parted command to erase the usb flash drive?[/QUOTE]
Oh sorry I thought I'd told you about the fdisk command, glad you found it.

What would you rather do?  You don't need to reformat unless you want to change the filesystem.  

Try these commands to unmount and remount the USB disc
```
sudo umount /dev/sdc1
sudo mount /dev/sdc1 /media/usbdisk -t vfat -o iocharset=utf8,umask=000
```

Then try to access the files through the link on the desktop, can you delete those you need to?

---

### Post by PowerWCRulez on 2006-03-26
[QUOTE=Sutekh]Oh sorry I thought I'd told you about the fdisk command, glad you found it.

What would you rather do?  You don't need to reformat unless you want to change the filesystem.  

Try these commands to unmount and remount the USB disc
```
sudo umount /dev/sdc1
sudo mount /dev/sdc1 /media/usbdisk -t vfat -o iocharset=utf8,umask=000
```

Then try to access the files through the link on the desktop, can you delete those you need to?[/QUOTE]

Ah, much better now, it's work great, the all files deleted and moved into trash box.. and I turned on the hidden file and I clicked the trash file to dump out it's all clean on my USB flash drive :) :) :)

---

### Post by Sutekh on 2006-03-27
Ok great!

---

### Post by Chickenfoot on 2006-10-15
Hey,

I typed in:

Re: Mount USB Flash drive
If you type on a terminal something like

Quote:
sudo mount /dev/sdd1 /media/usbdisk 

But I get this:

chickenfoot@spanky:~$ sudo mount /dev/sdd1 /media/usbdisk
Password:
mount: you must specify the filesystem type

Then I try:

chickenfoot@spanky:~$ sudo fdisk-l

And I egt this:  

sudo: fdisk-l: command not found
 
what's going on?

---

### Post by Sutekh on 2006-10-15
> **Chickenfoot said:**
> 

Then I try:

chickenfoot@spanky:~$ sudo fdisk-l

And I egt this:  

sudo: fdisk-l: command not found
 
what's going on?
If what you typed in your post is exactly what you typed in on your PC, then you need to add a space between the fdisk and the -l
```
sudo fdisk -l
```Then we should be able to sort the mount command.

---

