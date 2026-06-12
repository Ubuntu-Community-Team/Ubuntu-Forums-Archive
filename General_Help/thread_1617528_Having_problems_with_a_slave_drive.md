---
title: "Having problems with a slave drive"
date: 2010-11-09
forum: General Help
---

### Post by RiceReaper on 2010-11-09
Hello,


I'm fairly new to linux in general, im making strides, and I decided to buy a 500gb harddrive to run as a slave, for the increasing amount of data I store, and I cant use it. I tried to follow a PsychoCats tutorial, and while it was informative, I either did something wrong, or I did'nt understand. 

WIth Gparted I managed to format it with Ext4. IT shows up in my diskspace widgit as /dev/sdb1. But states it isnt accessable, and has a total drive space of 0mb.

Could someone help with this task. I dont need anything fancy. I just want it to read and write properly.

Thanks in advance.

---

### Post by RiceReaper on 2010-11-10
Okay.....

I booted my computer today and Suddenly the drive READS, however it still doesnt write, and from I can tell. a lack of permission to do so. It suddenly contains one inaccesable folder called lost+found.

No idea what is happening to me, any help will be very appreciated

---

### Post by TeoBigusGeekus on 2010-11-10
Try

```
sudo chown yourusername /dev/sdb2
```

---

### Post by RiceReaper on 2010-11-10
Thanks for the response.

the problems arise.

chown: cannot access `/dev/sdb2' no such file or directory exists.

---

### Post by TeoBigusGeekus on 2010-11-10
Ok then, mount the drive, type
```
mount
```
and post us the results.

---

### Post by RiceReaper on 2010-11-10
Okay.

My last post was actually a screw up, the device is called sdb1 not 2, and I typed 2. So I redid that one

```
myron@Kubuntu:~$ sudo chown myron /dev/sdb1
myron@Kubuntu:~$ mount -l /dev/sdb1
mount: according to mtab, /dev/sdb1 is already mounted on /media/eb522f10-938b-4ccd-840f-98ff00b9f006
mount failed
myron@Kubuntu:~$ 

```

---

### Post by TeoBigusGeekus on 2010-11-10
Alright, can you write to the drive now?

---

### Post by RiceReaper on 2010-11-10
Doesnt do anything. the lost+found folder only states on the bottom when you click it
could not enter folder
/media/eb522f10-938b-4ccd-84of-98ff00b9f006/lost+found.

I can't delete that folder, or add any new ones. If I attempt to drag in a folder from my first disk, it tells me access is denied.

---

### Post by TeoBigusGeekus on 2010-11-10
Post us the contents of /etc/fstab

---

### Post by RiceReaper on 2010-11-10
probably did this wrong

```
myron@Kubuntu:~$ /etc/fstab
bash: /etc/fstab: Permission denied
myron@Kubuntu:~$ 

```

Like I stated before, I did do a bunch of stuff from a tutorial, im not sure if I did anything wrong. 

I used this.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I followed it line for line, with the exception of editing anything UUID.

---

### Post by TeoBigusGeekus on 2010-11-10
```
gedit /etc/fstab
```
Copy the contents and paste them here.

---

### Post by RiceReaper on 2010-11-10
Had to install this, didnt have it.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ba9e1f10-7e9b-40f9-818d-9c750fadca2f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b56cb3b3-cd6c-4331-8e48-ea996345befc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by TeoBigusGeekus on 2010-11-10
Perfect. Now post us the output of
```
blkid
```

---

### Post by RiceReaper on 2010-11-10
```
myron@Kubuntu:~$ blkid
/dev/sdb1: UUID="eb522f10-938b-4ccd-840f-98ff00b9f006" TYPE="ext4" 

```

---

### Post by TeoBigusGeekus on 2010-11-10
Close gedit and reopen it with this command
```
gksu gedit /etc/fstab
```

Add this line at the end of the file
```
UUID=eb522f10-938b-4ccd-840f-98ff00b9f006 /media/disk ext4 relatime 0 2
```

Save and exit.

Finally
```
sudo mkdir /media/disk
```
and reboot.

Post us with the results.

---

### Post by RiceReaper on 2010-11-10
Okay I think were getting somewhere

That disk is now called simply disk. however it doesnt write still

upon starting kubuntu, I was asked for a password for KdeSudo, upon entering it, 
root> media > eb522f10-938b-4ccd-840f-98ff00b9f006 opened.

---

### Post by TeoBigusGeekus on 2010-11-10
For some reason the drive is owned by root.
Try 
```
sudo chown myron /media/disk
```
one more time.

---

### Post by RiceReaper on 2010-11-10
Ooooohhhhhhhhhhhh.

It works now hahaha.

Thanks a million man. I appreciate your time.

Lost+found is still there and not reading but. Im not going to mess around with that

---

### Post by TeoBigusGeekus on 2010-11-10
You're welcome.
Don't forget to mark the thread as solved.

---

### Post by TeoBigusGeekus on 2010-11-10
> **RiceReaper said:**
> Ooooohhhhhhhhhhhh.

It works now hahaha.

Thanks a million man. I appreciate your time.

Lost+found is still there and not reading but. Im not going to mess around with that

Don't worry about the lost and found folder. It is the place where corrupted files are placed when they are found during a filesystem check and it's perfectly normal that you can't access it.

---

