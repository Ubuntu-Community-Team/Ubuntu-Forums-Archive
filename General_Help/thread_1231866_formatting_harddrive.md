---
title: "formatting harddrive"
date: 2009-08-05
forum: General Help
---

### Post by twiltse on 2009-08-05
I am new to linux but not to computers! I am trying to add a 2nd hard drive to my linux box That is on a windows xp network. I have partitioned and formatted in fat32 using gparted. mounted the drive, shows up on my desktop. I launch filebrowser, I cannot copy anything to this drive.  I right click on the drive and only properties isn't grey out. I go to properties, permissions and everything is greyed out. owner: root, group root. Everything is greyed out. onthe bottom it says I am not the owner so I cannot change these permissions.  I bring up terminal and run:

todd@todd-Linux:~$ sudo chown -R USERNAME:todd /media/mynewdrive 
chown: invalid user: `USERNAME:todd'

todd@todd-Linux:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6a6f6a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2325    18675531   83  Linux
/dev/sda2            2326        2431      851445    5  Extended
/dev/sda5            2326        2431      851413+  82  Linux swap / Solaris

Disk /dev/sdb: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c3e7c3e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         784     6297448+   b  W95 FAT32

any help would be appreciated!! THX

---

### Post by Yvan300 on 2009-08-05
The permission problem is typical of most live cd sessions. I do not know how to solve the permissions problem at the moment.

---

### Post by lindsay7 on 2009-08-05
If sdb is the second drive, it looks like it is only 6448 megs. Which does not sound correct. Are you sure that you formated the whole drive? Try starting up your computer with a live Ubuntu cd or download Gparted and burn it to a disk. You can start your computer with it.  Make sure the new drive is unmounted and reformat it again.

---

### Post by twiltse on 2009-08-05
It is a 6 gig hdd, my 80 gig and 250 gig all do the same thing!! this is a permissions thing!! I just don't know enough about it to figure it out!!

---

### Post by bodhi.zazen on 2009-08-05
With fat and ntfs partitions , permissions are set at the time of mounting.

You can specify options when you mount the device

sudo mount /dev/adb1 /media/sdb1 -o uid,gid,umask

Or write a line in /etc/fstab

See : [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

### Post by twiltse on 2009-08-05
A little vague but I eventually got it! that sure seems like a lot of work just to install another harddrive!! I'm new to ubuntu and linux for that matter, but 12 hours of work! WOW!! Seems Gparted has a long way to go before it is a complete app!! OH!
 
I went gksu gedit /etc/fstab 

then added in fstab file:
/dev/sdb1    /media/mynewdrive   vfat    user,auto,fmask=0111,dmask=0000
I believe vfat and user is what fixed it! Just a guess though!

Thanks again!

---

