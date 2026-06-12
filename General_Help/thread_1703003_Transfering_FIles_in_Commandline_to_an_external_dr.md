---
title: "Transfering FIles in Commandline to an external drive."
date: 2011-03-08
forum: General Help
---

### Post by luciferactual on 2011-03-08
I would like to transfer some files on my internal hdd (via command line) to an external USB hdd and I need a little assistance.

 I know how to *cp -r /home/pictures to "destination" *but I can't seem to get my crippled system to see an external usb hdd drive. I tried reading the etc/fstab, but the external USB hdd drive would/could not report a drive name (example; /sdb1). 

How do I manually mount the external so I can finish the string to transfer the files to the external?

---

### Post by ezsit on 2011-03-08
To manually mount the external hard drive, first, find out what device name it has:

**sudo fdisk -l**
*that is a lower case L*

Assuming your drive is /dev/sdb1,

Create a mount point:

**sudo mkdir /mnt/extdrive**
**sudo mount /dev/sdb1 /mnt/extdrive**

And, so you as a regular user can copy files to your newly mounted hard drive, change the ownership of the mountpoint to your current user:

**sudo chown -R username:username /mnt/extdrive**

Where username is your current username. Now you can copy files:

**cp -r /home/pictures /mnt/extdrive/**

It should work.

---

### Post by luciferactual on 2011-03-09
> **ezsit said:**
> To manually mount the external hard drive, first, find out what device name it has:

**sudo fdisk -l**
*that is a lower case L*

Assuming your drive is /dev/sdb1,

Create a mount point:

**sudo mkdir /mnt/extdrive**
**sudo mount /dev/sdb1 /mnt/extdrive**

And, so you as a regular user can copy files to your newly mounted hard drive, change the ownership of the mountpoint to your current user:

**sudo chown -R username:username /mnt/extdrive**

Where username is your current username. Now you can copy files:

**cp -r /home/pictures /mnt/extdrive/**

It should work.

[ezsit]("http://ubuntuforums.org/member.php?u=74119")

You. Are. A. God!

Worked like a charm. Saved all my data. Thank you very much! Cheers.

---

