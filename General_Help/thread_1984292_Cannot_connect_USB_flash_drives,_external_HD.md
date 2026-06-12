---
title: "Cannot connect USB flash drives, external HD"
date: 2012-05-21
forum: General Help
---

### Post by jlh68 on 2012-05-21
I cannot connect any of my flash drives via USB.  I get the following error message: 

> Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmsg | tail give the following:

> john@NightHawk:~$ dmesg | tail
[ 2478.178413] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 2478.178421] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2478.182137] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2478.182146]  sdb: sdb1
[ 2478.187268] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2478.187276] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[ 2478.301923] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[ 2534.418408] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[ 2646.435024] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[ 2680.374443] usb 2-1.2: USB disconnect, address 5
john@NightHawk:~$ 


I don't know why on USB computer is looking for ext4 filesystem instead of VFAT?

---

### Post by kanikilu on 2012-05-21
Are you trying to mount these manually? If so, what's the command you are using? If not, where are you seeing this error?

A search of the error message came up with a similar thread here ([http://ubuntuforums.org/showthread.php?t=1524759](http://ubuntuforums.org/showthread.php?t=1524759)) that seemed to be related to entries in fstab. Can you post the contents of this file: /etc/fstab

---

### Post by jlh68 on 2012-05-22
No, not manually, automatically when inserted into the USB port, like it used to do before.  Before I tried to mount a WD "Elements" external HD, that would not mount.  Somehow it appears that I changed something in the OS that has caused no USB devices to mount either automatically or manually.

I have a persistent sdb1 in my /media file that I cannot remove.  The error I get with it is that sdb1 is not present. I was trying to get the WD 320-GB HD to work so that I can back-up and then do a new install of 12.04LTS and be done with 10.10. I do have a partition for /home so I might be able to install 12.04LTS without any problems to my data.

---

### Post by kanikilu on 2012-05-22
Hmm, I'm not sure, but hopefully someone else can suggest something. Also, more information would be more useful than less information...

Can you copy and paste the output of the following commands?

```
sudo fdisk -l
```
```
cat /etc/fstab
```
```
ls -l /media
```

---

### Post by jlh68 on 2012-05-23
As requested

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xfe282769

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1698    13631488   27  Unknown
/dev/sda2   *        1698        1710      102400    7  HPFS/NTFS
/dev/sda3            1710        6300    36864000    7  HPFS/NTFS
/dev/sda4            6300       38914   261970945    5  Extended
/dev/sda5            6300        6361      487424   83  Linux
/dev/sda6            6361        6871     4100096   82  Linux swap / Solaris
/dev/sda7            6871       10518    29295616   83  Linux
/dev/sda8           10519       38914   228084736   83  Linux
 
john@NightHawk:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid  0  0  
# / was on /dev/sda7 during installation
UUID=1ac2efbb-1409-4878-89d5-1aaa7b9d891d  /            ext4  errors=remount-ro    0  1  
# /boot was on /dev/sda5 during installation
UUID=f62ec458-671d-4fd2-a09d-a49a4b221b72  /boot        ext4  defaults             0  2  
# /home was on /dev/sda8 during installation
UUID=f63eadad-6024-4da2-a3cb-725b9e93db45  /home        ext4  defaults             0  2  
# swap was on /dev/sda6 during installation
UUID=546f9a8e-a173-41ff-8d94-8886cf8d5d37  none         swap  sw                   0  0  
/dev/sdb1                                  /media/sdb1  ext4  noauto,user          0  0  

john@NightHawk:~$ ls -l /media
total 40
drwxr-xr-x 2 root root 4096 2012-05-02 10:16 floppy
drwxr-xr-x 2 root root 4096 2012-05-18 13:09 sdb1
lrwxrwxrwx 1 root root    4 2012-05-21 14:33 usb -> usb0
drwxr-xr-x 2 root root 4096 2012-05-21 14:33 usb0
drwxr-xr-x 2 root root 4096 2012-05-21 14:33 usb1
drwxr-xr-x 2 root root 4096 2012-05-21 14:33 usb2
drwxr-xr-x 2 root root 4096 2012-05-21 14:33 usb3
drwxr-xr-x 2 root root 4096 2012-05-21 14:33 usb4
drwxr-xr-x 2 root root 4096 2012-05-21 14:33 usb5
drwxr-xr-x 2 root root 4096 2012-05-21 14:33 usb6
drwxr-xr-x 2 root root 4096 2012-05-21 14:33 usb7
john@NightHawk:~$ 


Okay- I discovered that if I plug in a USB device as a place holder then when I plug in the second USB device I can open it, ditto for the third USB device.  Device two is USB0 port, and device three is USB1 port and I presume that the fourth USB device would be USB3.  

I now looks like I need to be able to delete the sdb1 in the media file, also remove the floppy so that I can use my USB floppy drive.So how do I change the media file?

I hope you can help.
Thanks

---

### Post by kanikilu on 2012-05-23
Ok, I assume you don't have a separate ext4 partition or hard drive that you are wanting to mount to /media/sdb1? If so, first you'll want to remove the entry in fstab - or at least comment it out for now.

```
gksu gedit /etc/fstab
```

Scroll down to the last line and put a hash symbol (#) in front of it, so the line will now read:

```
#/dev/sdb1 /media/sdb1 ext4 noauto,user 0 0
```

Save and close the file. Now "refresh" the mounts:

```
sudo mount -a
```

Next delete the folder in /media (again, assuming here that there is nothing actually there):

```
sudo rm /media/sdb1
```

Now try a USB drive again...

---

### Post by jlh68 on 2012-05-23
Followed your suggestion:  I commented out the sdb1 and it no longer shows up in my Places menu.  Then I hit this problem, it says can not remove because it is a directory.  The system added it somehow, there should be a way to remove a directory.

> john@NightHawk:~$ gksu gedit /etc/fstab
john@NightHawk:~$ sudo mount -a
john@NightHawk:~$ sudo rm /media/sdb1
rm: cannot remove `/media/sdb1': Is a directory
john@NightHawk:~$ 

My USB flash drive shows up on the usb0 port, I can not drag a file into it. It also gives a "empty trash" notice, and then when clicked, I get a message that says:
> Unable to unmount usb0
umount: /media/usb0 is not in the fstab (and you are not root)

So my flash drives are not being treated like they used to when the name of the drive was listed on the desktop and I could drag files.

---

### Post by jlh68 on 2012-05-23
I noticed that I have in my /media directory sdb0, sdb1, ..... sdb7, and sdb, as well as floppy and sdb1.  I don't believe that any of those were there a week ago, which was prior to my trying to mount an usb floppy drive.

That is when I started screwing every thing up with the usb ports, when I tried to get the floppy drive to work.  I don't understand why the usb floppy drive didn't work like a flash drive as far as mounting.

---

### Post by kanikilu on 2012-05-23
> **jlh68 said:**
> I commented out the sdb1 and it no longer shows up in my Places menu.  Then I hit this problem, it says can not remove because it is a directory.  The system added it somehow, there should be a way to remove a directory.

Oh right, it's a directory, so do:

```
sudo rmdir /media/sdb1
```

If it's empty, that should work - I don't like suggesting rm -rf, but you can use that instead if all else fails (double-check that it's empty first before using that).

Honestly, I don't really know why USB drives still aren't mounting correctly, though. What does the *mount* command show when you plug one in?

---

### Post by jlh68 on 2012-05-24
I used rmdir last night while waiting for your reply and removed all directories in the /media dir.  
That made my flash drives work, my usb external HD work, and I found a way to mount my usb floppy drive, using the code below.

> udisks --mount /dev/sdb

On the floppy I have to mount it with the insertion of each floppy disk used.  Funny it won't load corrupted files.  Maybe I had something magnetic near one of my floppy discs.  I hadn't looked at them since 1999.  I intend to capture my files from the floppy disks and burn to a CD-R or DVD+R for archiving.

**kanikilu** - I really appreciate your help and interest in my problem.  You have helped me in several ways, one to correct problem, secondly I worked around and figured some things out from your prompting.  Isn't Linux great?  You can break it in either major ways or minor ways, and with patience, perseverance, and listening to others, we can un-break the system and get it working again.  Thanks for your help.

---

### Post by kanikilu on 2012-05-24
No problem, glad you got it working :)

It's been a long time since I've used a floppy, but I do remember that it has to be mounted each time.

---

### Post by jlh68 on 2012-05-24
Once I get all the files archived off my floppies, I don't expect that I will use the floppy drive much either.

---

