---
title: "Disk Permissions"
date: 2009-10-11
forum: General Help
---

### Post by am6465 on 2009-10-11
I recently switched from OSX to Mac. I have two hard drives that I had been using in the mac. One is a regular external hard drive and one was the internal hard drive of my last laptop that I put in an enclosure. The problem is that the external hard drive only has read permissions and the other one doesn't give me any permissions. How can I change these permissions?

---

### Post by 3rdalbum on 2009-10-11
In Nautilus (you might need to open it as root), change the permissions of the folder that contains the disks. For instance, if the disk has mounted under /media/disk, change the permissions of /media/disk.

If any of your hard disks are formatted as HFS+ (I expect the internal will be) then you need to use Apple's Disk Utility to disable journalling before it can be written to in Linux.

---

### Post by s.fox on 2009-10-11
Hello,

[This]("https://help.ubuntu.com/community/FilePermissions") should be able to help you.  If you require any further help please post back :)

-Silver Fox

---

### Post by am6465 on 2009-10-11
I tried both of those things. First I tried changing things via command line. This is what I got:

amustafa@amustafa-laptop://media/Mustafa$ ls -l\
> 
total 10493568
-rw-r--r-- 1 99 99 10737419516 2009-05-03 12:38 AM2.dmg
drwxr-xr-x 1 99 99          49 2009-08-19 00:28 amustafa
drwxrwxrwx 1 99 99          15 2009-04-13 22:18 Applications
-rw-r--r-- 1 99 99        1024 2008-06-05 13:42 Desktop DB
-rw-r--r-- 1 99 99           2 2008-06-05 13:41 Desktop DF
drwxr-xr-x 1 99 99          18 2009-01-19 21:59 Documents
drwxr-xr-x 1 99 99           7 2009-01-27 01:31 Downloads
drwxrwxr-x 1 99 99         238 2009-04-05 23:34 Fonts
drwxr-xr-x 1 99 99           5 2008-06-25 18:03 guides
drwxr-xr-x 1 99 99           8 2008-06-05 17:27 iTunes
drwxr-xr-x 1 99 99           4 2009-04-24 01:33 OneTouch Backup
drwxr-xr-x 1 99 99           6 2009-01-27 01:36 Other
drwxr-xr-x 1 99 99           5 2009-01-06 14:17 untitled folder 2
drwxrwxrwx 1 99 99           6 2009-05-07 23:44 Video
amustafa@amustafa-laptop://media/Mustafa$ chmod g+w amustafa/
chmod: changing permissions of `amustafa/': Read-only file system
amustafa@amustafa-laptop://media/Mustafa$ sudo chmod g+w amustafa
[sudo] password for amustafa: 
chmod: changing permissions of `amustafa': Read-only file system
amustafa@amustafa-laptop://media/Mustafa$ cd ..
amustafa@amustafa-laptop://media$ ls
cdrom  cdrom0  cdrom1  disk  Mustafa
amustafa@amustafa-laptop://media$ sudo chown amustafa Mustafa
chown: changing ownership of `Mustafa': Read-only file system
amustafa@amustafa-laptop://media$ sudo chown amustafa-laptop Mustafa
chown: invalid user: `amustafa-laptop'
amustafa@amustafa-laptop://media$ sudo chown amustafa Mustafa
chown: changing ownership of `Mustafa': Read-only file system
amustafa@amustafa-laptop://media$ 


and when I tried it in nautilus I got the same things. Both were run using "sudo"

---

