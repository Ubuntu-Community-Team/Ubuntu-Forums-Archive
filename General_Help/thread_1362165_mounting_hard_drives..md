---
title: "mounting hard drives."
date: 2009-12-22
forum: General Help
---

### Post by windowsfree on 2009-12-22
I have a desktop PC with 2 hard drives.  The 1st drive has ubuntu 9.10 loaded on it.  The second drive is formatted as a Vfat drive.  How can I mount the second drive at boot up so I don't have to click on it and enter the password to mount it?  
Thanks!

---

### Post by aktiwers on 2009-12-22
You can add it to your fstab.

First find the name of the drive:
```
df -h
```It might be something like /dev/sda. 

Then create a folder to mount it on:
```
sudo mkdir /media/SOMENAME
```change SOMENAME to what you like
Then edit fstab:
```
sudo gedit /etc/fstab
```And add:
```
/dev/sda /media/SOMENAME vfat auto,users,nosuid,rw 0 0
``` to the end of the file and save. It should now mount on boot.

---

### Post by windowsfree on 2009-12-23
Thanks, that worked, I was making one big mistake each time.  I put the name of the drive in my fstab file as sdb instead of sda.  thanks again

---

### Post by Mahngiel on 2009-12-23
thanks, works. *thumbs up*

---

### Post by abhilashm86 on 2009-12-23
you can use ntfs-config also, it automatically detects drives and mounts permanently.......
```
sudo apt-get install ntfs-config 

```

---

### Post by Conzo on 2009-12-24
You also Can Mount Network drives in the fstab also ,,The lines in red are network drives 



Here my fstab 



# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=46aa1fdd-43f9-4776-89e2-b122923fa6b3 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=171208ae-43de-46db-b06f-507f109f6215 none            swap    sw              0       0
/dev/scd0     /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0 
/dev/sdb1    /media/storage   ext4    defaults     0        2
[COLOR=Red]//192.168.1.67/brandon  /media/brandon  cifs      0       0
//192.168.1.64/Jeri  /media/Jeri  cifs user=jeri,password=xxxxxxxxxx     0       0
[/COLOR] 


On reboot My Network drives load up ...

Conzo

---

### Post by windowsfree on 2009-12-24
Works 90% of the time.  After 10 startups, only once did it not mount the drive....I don't understand the inconsistency.

---

