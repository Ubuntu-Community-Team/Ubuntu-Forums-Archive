---
title: "Trouble mounting an external hard drive"
date: 2009-08-10
forum: General Help
---

### Post by XxionxX on 2009-08-10
I was following the instructions for mounting a disk (The file system is fat 32) and I don't know what is wrong. I can't run

```
sudo fdisk -l
```

This just keeps running half way through and I don't know what that means. 
The disk says that it is already mounted but I cannot access the files in the /media/windsk/ directory. All I get is an error message that says

```

Unable to mount 82.0 GB Media

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```

and I can't unmount it either. I get the same result if I restart the computer.

---

### Post by XxionxX on 2009-08-12
Well I am going on vacation with my family until Monday. So I won't be able to reply to anyone.:(

---

### Post by XxionxX on 2009-08-17
I'm back from vacation! I would love to fix this soon!

---

### Post by cariboo on 2009-08-17
How is the partition formated? If it is ntfs try running chkdsk on it in Windows.

---

### Post by XxionxX on 2009-08-17
The file system is FAT32.

---

### Post by stinger30au on 2009-08-18
try this

click applications, add remove software, and set it to show all available s/w

search on

management

scroll down and put a tick in box "disk management"

also just ot be on the safe side, do a search on "ntfs"

put a tick in thew box "ntfs configuration tools"

click apply and let both add themself to pc

if you click applicatoins, system tools, you will find disk management

and under system, administration u will find ntfs config tools

hope this helps

---

### Post by XxionxX on 2009-08-18
This didn't work, I just got an error message that said.

```

There are no filesystems which you are allowed to mount or unmount.
Contact your administrator.

```

I thought that I might try to log in as a root user and try again but it's late, so I'll try again tomorrow.

---

### Post by HiImTye on 2009-08-18
```
sudo apt-get update && sudo apt-get install pysdm
```

administration > storage device manager
enter your password
select your drive
click on the 'browse' icon to the right of 'mount point', choose your folder in /media/ to mount to
choose your options
click 'apply'

hope this helps :)

---

### Post by bchurchill on 2009-08-18
[FONT=Arial][SIZE=1]I'm not sure if you'll need this, but try

```

sudo apt-get install [/SIZE][/FONT][FONT=Arial][SIZE=1][B]fat-modules-2.6.28-11-generic-di
[/B][/SIZE][/FONT][FONT=Arial][SIZE=1]
```[/SIZE][/FONT]

and then to mount you'll need the instructions above to do it graphically, or do something like

```

sudo mount -t vfat /path/to/device /path/to/mount

```

---

### Post by XxionxX on 2009-08-21
[COLOR=Black]HiImTye when I tried to run the [/COLOR]storage device manager program it would not run. I tried several times but it wouldn't even give me an error message. Just nothing.
[COLOR=Black]
[/COLOR][COLOR=Black]bchurchill I ran the code you gave me several times in different forms but I could not install the [/COLOR] fat-modules-2.6.28-11-generic-di and I kept getting the same error message.
[COLOR=Black]
[/COLOR]```

sudo apt-get install fat-modules-2.6.28-11-generic-di
[sudo] password for xion: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fat-modules-2.6.28-11-generic-di

```[COLOR=Black][/COLOR]

---

### Post by XxionxX on 2009-08-22
Update: I tired the storage device manager again (I am able to boot the program up when the drive isn't attached) and when I attached the external hard drive I got this message again.

```

Unable to mount 82.0 GB Media

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

```

---

### Post by XxionxX on 2009-08-22
> **bchurchill said:**
> [FONT=Arial][SIZE=1]I'm not sure if you'll need this, but try

```

sudo apt-get install 
```[/SIZE][/FONT]```
[FONT=Arial][SIZE=1][B]fat-modules-2.6.28-11-generic-di
[/B][/SIZE][/FONT]
```

and then to mount you'll need the instructions above to do it graphically, or do something like

```

sudo mount -t vfat /path/to/device /path/to/mount

```
I tried this again with the same error messages. But this time I noticed that I can "see" the hard drive (total space and that the computer detects it). But I cannot see the filesystem. I noticed this when I tried to skip to the last step in the above suggestion. I know where I am supposed to mount it to, but I cannot access the external hard drives filesystem.

---

### Post by XxionxX on 2009-08-23
Ok, I seem to be able to mount other volumes besides this one because I was able to mount a thumb drive with no problems. I was able to mount and retrieve the pictures without any of the problems that I am having with my external hard drive. Anyone??

---

### Post by scouser73 on 2009-08-23
Try this tutorial: [[COLOR="Red"]**Ubuntu: Mount External Hard Disk**[/COLOR]]("http://www.blog.highub.com/linux/ubuntu-mount-external-hard-disk/")

---

### Post by XxionxX on 2009-08-23
I tried the command on that toutorial and all I got was this:

```
 sudo lsusb
Bus 002 Device 003: ID 0d49:5010 Maxtor 5000LE Drive
Bus 002 Device 002: ID 1020:0006 Labtec 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```It still won't let me access the drive. I have even moved it to different usb ports to see if I had a bad connection. Nothing.:-k
The Labtec is my keyboard and the Maxtor 5000LE Drive is my external hard drive.

Edit:
I was trying other things to mount the drive and I thought that this might help someone understand my problem. I was going through one of the many tuotorials on the net on how to mount a drive and I tried this command again:

```

sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ca10ca0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extended
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

```and I realized that it was freezing half way thorough. It shows my computers filesystem but not the external HD. I hope that means something to someone because I have no idea what it means.

Edit2:
I was following this thread([http://www.linuxforums.org/forum/debian-linux-help/43108-cant-mount-fat-32-ubuntu.html](http://www.linuxforums.org/forum/debian-linux-help/43108-cant-mount-fat-32-ubuntu.html)) when I ran this code in a terminal:
```

sudo mkdir /media/windows
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab

```And then I added this to the fstab file:
```

/dev/sdb1   /media/windows  vfat  noauto,users,rw,exec   1  0

```When I did this the name of the the HD changed from 'disk' to 'windows'. Once again I have no idea what this means.

I also found out from a program called MountManager 0.2.6 that the HD is located here /dev/sdb1. The funny thing is that the MountManager software says that the HD is mounted and the file browser says that it is not.](*,)

---

### Post by XxionxX on 2009-08-23
I ran this code and got this error message:

```

sudo mount /dev/sdb1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

mount: /dev/sdb1 already mounted or /media/windows/ busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/windows

```

If it's already mounted then what is happening??:confused:

---

### Post by XxionxX on 2009-08-25
I don't think that I can describe my problem any further. Really? I mean this is where linux fails? An external hard drive?

---

### Post by XxionxX on 2009-09-13
I am bumping this thread because I still haven't solved this issue.

---

### Post by XxionxX on 2009-09-18
I am bumping this thread again.

---

### Post by XxionxX on 2009-10-12
I feel foolish bumping this thread yet again. I really think that this is futile. This community doesn't seem to value my membership. I really wanted to be part of the Linux community that I had heard so much about. I can understand that no one seems to have time for noobs, but I haven't received ANY comments on my problem. I am very patient, I know that this is free software, and I have expected nothing other than a hope to make friends in the programming community.

---

