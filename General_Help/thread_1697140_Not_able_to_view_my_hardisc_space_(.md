---
title: "Not able to view my hardisc space :("
date: 2011-02-28
forum: General Help
---

### Post by buntys006 on 2011-02-28
Hello friends, I'm new to Ubuntu, I've just installed Ubuntu with advanced partitions. 
I'm not able to view my secondary disc space. 
I've used the command sudo fdisk -l

and this is what I got 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ac5ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3040    24413184   83  Linux
/dev/sda2            3040       19458   131874817    5  Extended
/dev/sda5           19215       19458     1952768   82  Linux swap / Solaris
/dev/sda6           13136       19215    48828416   83  Linux
/dev/sda7            3040       13136    81092608   83  Linux

Partition table entries are not in disk order



though it shows I have disc space, I'm not able to access. 

Please help.


regards,
Vikram

---

### Post by TeoBigusGeekus on 2011-02-28
What's the space you cannot access?
Post us the output of
```
df -h
```

---

### Post by hawkmage on 2011-02-28
Looking at the output of the fdisk command you have a drive with 19458 cylinders and the partitions you have use all of these cylinders.  So your partitions fill your drive /dev/sda.

Where is this disk space that you can't access?

---

### Post by buntys006 on 2011-02-28
Thanks for your replies.

I'm just able to access 25GB of the space , which was created as main partition.

I'm not able to access any of my secondary partitions. 

here is the o/p for 
df -h

vikram@vikram-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              23G  6.0G   16G  28% /
none                  492M  276K  492M   1% /dev
none                  497M  2.8M  494M   1% /dev/shm
none                  497M   88K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda6              46G  180M   44G   1% /data
/dev/sda7              77G  180M   73G   1% /data2

infact I'm not able to see that i have other disc space

---

### Post by TeoBigusGeekus on 2011-02-28
Can't you reach sda6 and 7 from the places menu?

---

### Post by buntys006 on 2011-02-28
> **TeoBigusGeekus said:**
> Can't you reach sda6 and 7 from the places menu?


yaa, its not in places and in computer as well :(

---

### Post by hawkmage on 2011-02-28
Your df -h shows those partitions mounted as "/data" and "/data2".  What do you get if you type the following in at a command prompt:
```
ls -la /data
ls -la /data2
```

---

### Post by buntys006 on 2011-02-28
> **hawkmage said:**
> Your df -h shows those partitions mounted as "/data" and "/data2".  What do you get if you type the following in at a command prompt:
```
ls -la /data
ls -la /data2
```


here is the output 

vikram@vikram-desktop:~$ ls -la /data
total 24
drwxr-xr-x  3 root root  4096 2011-02-28 21:33 .
drwxr-xr-x 24 root root  4096 2011-02-28 21:50 ..
drwx------  2 root root 16384 2011-02-28 21:33 lost+found
vikram@vikram-desktop:~$ ls -la /data2
total 24
drwxr-xr-x  3 root root  4096 2011-02-28 21:33 .
drwxr-xr-x 24 root root  4096 2011-02-28 21:50 ..
drwx------  2 root root 16384 2011-02-28 21:33 lost+found

---

### Post by TeoBigusGeekus on 2011-02-28
Oh I see.
You have specified the mount points of your 2 partitions as
```
/data
```
and
```
/data2
```
Gnome recognises partitions mounted on /media.
Post us the contents of your fstab file.
```
gksu gedit /etc/fstab
```

---

### Post by hawkmage on 2011-02-28
So, that indicates to me that the partitions are mounted and accessible.  

Go to Places and choose "Computer" then click on "Filesystem" in the lest on the left.  Do you see folders named "data" and "data2"?

---

### Post by buntys006 on 2011-02-28
> **TeoBigusGeekus said:**
> Oh I see.
You have specified the mount points of your 2 partitions as
```
/data
```and
```
/data2
```Gnome recognises partitions mounted on /media.
Post us the contents of your fstab file.
```
gksu gedit /etc/fstab
```

here it is :) 

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=bd815428-5f37-4bf0-b99b-d456e7aae4fa /               ext4    errors=remount-ro 0       1
# /data was on /dev/sda6 during installation
UUID=b1f3c2ef-b44e-4d80-aa9d-905f42fd80ce /data           ext4    defaults        0       2
# /data2 was on /dev/sda7 during installation
UUID=8715b409-af76-4b21-8c10-e388e31d08cb /data2          ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=f27110bf-197b-400f-bfa0-e8a62902aec2 none            swap    sw              0       0

---

### Post by TeoBigusGeekus on 2011-02-28
```
sudo mkdir /media/data /media/data2
```
Then
```
gksu gedit /etc/fstab
```
Change these lines
```
# /data was on /dev/sda6 during installation
 UUID=b1f3c2ef-b44e-4d80-aa9d-905f42fd80ce /data ext4 defaults 0 2
 # /data2 was on /dev/sda7 during installation
 UUID=8715b409-af76-4b21-8c10-e388e31d08cb /data2 ext4 defaults 0 2
```
to
```
# /data was on /dev/sda6 during installation
 UUID=b1f3c2ef-b44e-4d80-aa9d-905f42fd80ce /media/data ext4 defaults 0 2
 # /data2 was on /dev/sda7 during installation
 UUID=8715b409-af76-4b21-8c10-e388e31d08cb /media/data2 ext4 defaults 0 2
```
Save, reboot, post back.

---

### Post by aktiwers on 2011-02-28
Haha nice avatar TeoBigusGeekus..

Bunty remember to mark the threat as solved after you rebooted ;)

or if you dont want to reboot, type:

```
sudo mount -a
```

---

### Post by buntys006 on 2011-02-28
> **TeoBigusGeekus said:**
> ```
sudo mkdir /media/data /media/data2
```Then
```
gksu gedit /etc/fstab
```Change these lines
```
# /data was on /dev/sda6 during installation
 UUID=b1f3c2ef-b44e-4d80-aa9d-905f42fd80ce /data ext4 defaults 0 2
 # /data2 was on /dev/sda7 during installation
 UUID=8715b409-af76-4b21-8c10-e388e31d08cb /data2 ext4 defaults 0 2
```to
```
# /data was on /dev/sda6 during installation
 UUID=b1f3c2ef-b44e-4d80-aa9d-905f42fd80ce /media/data ext4 defaults 0 2
 # /data2 was on /dev/sda7 during installation
 UUID=8715b409-af76-4b21-8c10-e388e31d08cb /media/data2 ext4 defaults 0 2
```Save, reboot, post back.

hey.. i can see them now, you guys rock 
between i have a folder in it by name "lost+found"
what is it?? can i delete it ?

---

### Post by TeoBigusGeekus on 2011-02-28
It's a special folder where corrupt files will go whenever ubuntu's checks find some.
Don't touch it - you can't anyway.
Don't forget to mark the thread as solved.

---

### Post by hawkmage on 2011-02-28
Do not delete the "lost+found" directory.  It is a system folder that is in every partition/volume that is used to allocate unlinked "clusters" that are found by fsck.

---

### Post by buntys006 on 2011-02-28
> **TeoBigusGeekus said:**
> It's a special folder where corrupt files will go whenever ubuntu's checks find some.
Don't touch it - you can't anyway.
Don't forget to mark the thread as solved.


I'm not able to paste any thing in those disks.

n last Q how to mark it as solved. ?

I'm new to this

---

### Post by aktiwers on 2011-02-28
Hey I always delete the LOST+FOUND folder.

Just have a look in it first, and make sure no files you love are in there.

Lost and found is for your own files who has been lost or found during harddisc check. If nothings in there you like, I would delete it. Specially if its taking up a lot of space.

---

### Post by TeoBigusGeekus on 2011-02-28
> **buntys006 said:**
> I'm not able to paste any thing in those disks.



Come again? Can't you create new documents/folders in it?

---

### Post by aktiwers on 2011-02-28
> **buntys006 said:**
> I'm not able to paste any thing in those disks.

n last Q how to mark it as solved. ?

I'm new to this

```
sudo chown yourubuntuusername:yourubuntuusername -R /media/data /media/data2

sudo chmod 777 -R /media/data /media/data2

```

To mark thread solved go to "thread tools" in the upper right corner.

cheers

---

### Post by buntys006 on 2011-02-28
Yeah.. I'm not able to create any documents in them . 

those options are inactive.

---

### Post by TeoBigusGeekus on 2011-02-28
Do what aktiwers posted and post back.

---

### Post by buntys006 on 2011-02-28
You guys really 'ROCK', thank you so much :)..

---

### Post by TeoBigusGeekus on 2011-02-28
Glad to hear that.

---

