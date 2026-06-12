---
title: "Premission for hard drives"
date: 2012-07-23
forum: General Help
---

### Post by sorooshubu on 2012-07-23
Dear All

Why permissions of hard drives in /dev/sda* and mounted folders in /media/are  different?

ls -l /dev/ | grep sda  
brw-rw----  1 root    disk        8,   0 Jul 23 15:37 sda
brw-rw----  1 root    disk        8,   1 Jul 23 15:37 sda1
brw-rw----  1 root    disk        8,   2 Jul 23 15:37 sda2
brw-rw----  1 root    disk        8,   3 Jul 23 15:37 sda3
brw-rw----  1 root    disk        8,   5 Jul 23 15:37 sda5
brw-rw----  1 root    disk        8,   6 Jul 23 14:45 sda6
brw-rw----  1 root    disk        8,   7 Jul 23 14:45 sda7
brw-rw----  1 root    disk        8,   8 Jul 23 15:37 sda8
brw-rw----  1 root    disk        8,   9 Jul 23 15:37 sda9


ls -l /media/
drwx------ 16 soroosh soroosh 4096 Jul 22 17:35 Documents
drwx------  1 soroosh soroosh 4096 Jul 17 23:09 Entertainment
drwx------  1 soroosh soroosh 4096 Jul  5 17:08 System Reserved
drwx------  1 soroosh soroosh 8192 Jul 23 14:08 Win7

---

### Post by drmrgd on 2012-07-23
I might not have this 100% right, but I think it has to do with how they're mounted.  The entries in fstab should have a permissions mask that will affect the way /dev/sda/ is mounted.

---

### Post by TheFu on 2012-07-23
Ubuntu and other UNIX-like operating systems use a different file system than Windows.  Permissions capabilities are different between Linux (and other UNIX-like) file systems and NTFS which is used by Windows on hard drives.

[https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) might help.

When Linux mounts an NTFS or Fat32 or vFat or exFat partition, it has to guess which permissions you intend unless you specifically tell it what you want at the mount time.  With non-UNIX file systems, you can specify the default owner, group, file and directory permissions for this other file system types **when they are mounted**.

Ok, file that are inside /dev/ are special.  These provide raw access to hardware and we need to be extremely careful concerning those permissions and which accounts have access for security reasons.  Many of these devices can only be directly accessed by "root", so a helper program is needed so any general userid can make use of a device.  This is designed that way for security reasons.  Block devices, like /dev/sda* are directly useable only by root-owned processes for this same reason.

BTW, this is a fantastic question and understanding the answer fully will help you understand the internals of UNIX-like operating systems to a much, much deeper level than most people.  This recent article [http://www.howtogeek.com/117939/htg-explains-what-everything-is-a-file-means-on-linux/](http://www.howtogeek.com/117939/htg-explains-what-everything-is-a-file-means-on-linux/) will explain some more.

---

### Post by Chris Musampa on 2012-07-23
Short answer: The permissions are different because accessing the partitions in listed /dev is a completely different thing from accessing the file systems contained in those partitions.

Long answer: The above with bells on.:)

---

### Post by sorooshubu on 2012-07-26
> **TheFu said:**
> Ubuntu and other UNIX-like operating systems use a different file system than Windows.  Permissions capabilities are different between Linux (and other UNIX-like) file systems and NTFS which is used by Windows on hard drives.

[https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions](https://www.linux.com/learn/tutorials/309527-understanding-linux-file-permissions) might help.

When Linux mounts an NTFS or Fat32 or vFat or exFat partition, it has to guess which permissions you intend unless you specifically tell it what you want at the mount time.  With non-UNIX file systems, you can specify the default owner, group, file and directory permissions for this other file system types **when they are mounted**.

Ok, file that are inside /dev/ are special.  These provide raw access to hardware and we need to be extremely careful concerning those permissions and which accounts have access for security reasons.  Many of these devices can only be directly accessed by "root", so a helper program is needed so any general userid can make use of a device.  This is designed that way for security reasons.  Block devices, like /dev/sda* are directly useable only by root-owned processes for this same reason.

BTW, this is a fantastic question and understanding the answer fully will help you understand the internals of UNIX-like operating systems to a much, much deeper level than most people.  This recent article [http://www.howtogeek.com/117939/htg-explains-what-everything-is-a-file-means-on-linux/](http://www.howtogeek.com/117939/htg-explains-what-everything-is-a-file-means-on-linux/) will explain some more.

Thanks for answer, I think access for /dev/sda* is for access of filesystem,
But it's different, I must read more about this issue
these links are good point to start

---

### Post by sorooshubu on 2012-07-26
I read some tutorials about linux file permission, 
I think, I must rephrase my question,
Why a ext[2/4] partition mount with permission other than permission specified in /dev/sda*?
OR
How restrict read or write access of specified user for specified partition?

I find permission of dev file and mounted folder in media is different, there must be some option for mount in /etc/fstab file.

another question is:
How restrict specified user to can not mount a specified partition?

any help appreciated :)
SorooshUbu

---

### Post by sorooshubu on 2012-07-27
Hi

No one has a clue ?!!!!!!!

It must be simple, but i do not know.
please help me to find answer.

---

