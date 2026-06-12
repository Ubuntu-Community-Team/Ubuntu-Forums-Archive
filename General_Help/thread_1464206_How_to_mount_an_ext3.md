---
title: "How to mount an ext3?"
date: 2010-04-27
forum: General Help
---

### Post by zzz99 on 2010-04-27
Hi everyone,

I am new at ubuntu(linux).

I have a Western Digital World edition II network HDD, but somehow I have lost the Media folder...

I have also read [http://foremost.sourceforge.net/](http://foremost.sourceforge.net/) is a very great recovery tool in ubuntu, is this true?
[http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html](http://www.ubuntu-unleashed.com/2008/04/howtorecover-and-undelete-text-file-in.html)


So I have pull out the HD from the western digital NAS case and put it into a USB enclosure.
Anyone can teach me how to mount this driver?

To look for device boot name
sudo fdisk -l


But how to look for the mount_point_dir?

sudo mount /dev/sdc4 [mount_point_dir] -t ext3

Please advise.
Thanks.

---

### Post by limey_rick on 2010-04-28
The mount point is a directory you create or decide to mount he device to. Normally if you plug in a USB device, it will be recognized and automatically mounted. If you want to mount it manually, you can create a directory in /media and then use the mount command.

> sudo mkdir /media/wd_usb
> sudo mount /dev/sdc4 /media/wd_usb

You probably don't need to specify the file type because it will be recognized. 

When you plug the USB drive into the PC, does it not auto mount?

---

### Post by hopstah on 2010-04-28
If you're new to Linux, chances are the drive isn't in an ext* format.  But that's only a minor issue.  What the [mount_point_dir] means is simply an empty folder on your computer where you will be able to access the drive from.  Try this:```
sudo mkdir /media/usbdrive
```This will make a directory at /media/usbdrive.  Now run your ```
sudo mount /dev/sdc4 /media/usbdrive -t ntfs
``` and you should be able to access the drive at /media/usbdrive.  I'm assuming that /dev/sdc4 is what you got from running fdisk, and I'm also assuming that your drive is formatted as NTFS.  If fdisk tells you something different, change the 'ntfs' in the 'mount' command to the proper file system type.

---

### Post by hopstah on 2010-04-28
Too slow.....

---

### Post by zzz99 on 2010-04-28
Thanks for your help rick.

The driver icon show up but I can't get access to it.
[IMG]http://dl.dropbox.com/u/266708/NAS%20problem.JPG[/IMG]


I pull the HD out from Western Digital My book World edition II(Mirror/RAID1), I believe that is ext3?

I can't have it recognized in my Mac/PC...


> **limey_rick said:**
> The mount point is a directory you create or decide to mount he device to. Normally if you plug in a USB device, it will be recognized and automatically mounted. If you want to mount it manually, you can create a directory in /media and then use the mount command.

> sudo mkdir /media/wd_usb
> sudo mount /dev/sdc4 /media/wd_usb

You probably don't need to specify the file type because it will be recognized. 

When you plug the USB drive into the PC, does it not auto mount?

---

### Post by zzz99 on 2010-04-28
Thanks hopstah and this is what I got.

[IMG]http://dl.dropbox.com/u/266708/NAS%20problem%201.JPG[/IMG]
[IMG]http://dl.dropbox.com/u/266708/NAS%20problem%202.JPG[/IMG]


[SIZE="3"][COLOR="Orange"]By the way, do you guys think there will be a chance for me to recover those deleted files in this case? Should I just give it up... Please advise.[/COLOR]
[/SIZE]

> **hopstah said:**
> If you're new to Linux, chances are the drive isn't in an ext* format.  But that's only a minor issue.  What the [mount_point_dir] means is simply an empty folder on your computer where you will be able to access the drive from.  Try this:```
sudo mkdir /media/usbdrive
```This will make a directory at /media/usbdrive.  Now run your ```
sudo mount /dev/sdc4 /media/usbdrive -t ntfs
``` and you should be able to access the drive at /media/usbdrive.  I'm assuming that /dev/sdc4 is what you got from running fdisk, and I'm also assuming that your drive is formatted as NTFS.  If fdisk tells you something different, change the 'ntfs' in the 'mount' command to the proper file system type.

---

### Post by lordbux on 2010-04-28
```
sudo mkdir /media/usbdrive
```
This will make a directory at /media/usbdrive. Now run your
Code:
```
sudo mount /dev/sdc4 /media/usbdrive -t ext3
```

you can try using ext3 in place of -t ntfs , above code

---

### Post by zzz99 on 2010-04-28
Thanks lordbux.

This is what I got.

```
jack@jack-laptop:~$ sudo mount /dev/sdb4 /video/usbdrive -t ext3
mount: mount point /video/usbdrive does not exist
jack@jack-laptop:~$ sudo mount /dev/sdb4 /media/usbdrive -t ext3
mount: wrong fs type, bad option, bad superblock on /dev/sdb4,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

jack@jack-laptop:~$ sudo mount /dev/sdb4 /media/usbdrive -t ntfs
NTFS signature is missing.
Failed to mount '/dev/sdb4': Invalid argument
The device '/dev/sdb4' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
jack@jack-laptop:~$ 

```

> **lordbux said:**
> ```
sudo mkdir /media/usbdrive
```This will make a directory at /media/usbdrive. Now run your
Code:
```
sudo mount /dev/sdc4 /media/usbdrive -t ext3
```you can try using ext3 in place of -t ntfs , above code

---

### Post by limey_rick on 2010-04-28
The problem seems to be that the disk you are trying to mount is neither NTFS or ext3. You said that you pulled this from a NAS case, so what type of disk formats does this NAS case use? 

What is the NAS case? For example, is it possible that the NAS case has multiple disks in and they are configured in a Raid format?

---

### Post by zzz99 on 2010-04-28
This is a Western Digital my book world edition II, mirro(raid1)

[IMG]http://www.wdc.com/global/images/products/img2/300/wdfMyBook_World_H2N.jpg[/IMG]
[http://www.wdc.com/en/products/Products.asp?DriveID=589](http://www.wdc.com/en/products/Products.asp?DriveID=589)


> **limey_rick said:**
> The problem seems to be that the disk you are trying to mount is neither NTFS or ext3. You said that you pulled this from a NAS case, so what type of disk formats does this NAS case use? 

What is the NAS case? For example, is it possible that the NAS case has multiple disks in and they are configured in a Raid format?

---

### Post by limey_rick on 2010-04-28
So in this case, I don't know if Linux would recognize this disk. You are trying to mount this as a single disk, but its part of a pair of RAID disks, so you need to mount it as a FakeRaid disk.  

Please check this doc.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by limey_rick on 2010-04-28
Check out this post too. This is in line with what I am thinking, that is, your disk is part of a RAID set so it may have meta data on it that creates problems.

[http://ubuntuforums.org/showthread.php?t=1464246](http://ubuntuforums.org/showthread.php?t=1464246)

---

### Post by zzz99 on 2010-04-29
Thanks a lot rick.

I will read about that this weekend since that is a lot of new contents to me.

---

### Post by dino99 on 2010-04-29
MountManager is your boy  :P

---

### Post by zzz99 on 2010-04-30
Thanks for all the help guys.

unfortunately... my mbp hd corrupt as well last night... 

I will just give up those media files...

Thanks again.

---

