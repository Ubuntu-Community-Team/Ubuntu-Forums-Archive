---
title: "sda1 and sdb1 showing as the same?"
date: 2011-02-07
forum: General Help
---

### Post by eats7 on 2011-02-07
hey guys i'm having quite the time trying to automount both my windows partition and sd card on boot. when i go into pysdm, it shows that sda1(windows) is actually sdb1(which is my card) so my windows partition wont ever automount!!  driving me insane. heres a pic along with my fstab:
[IMG]http://img815.imageshack.us/img815/7919/screenshot1uk.png[/IMG]
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                    proc     nodev,noexec,nosuid  0  0  
#Entry for /dev/sda2 :
UUID=3c014022-8567-40c6-9aef-5dd1d6e135ed  /                        ext4     errors=remount-ro    0  1  
#Entry for /dev/sda1 :
UUID=A2825FFB825FD281                      /media/A2825FFB825FD281  ntfs-3g  users,user,owner     0  0  
Entry for /dev/sda5 :
UUID=741efd93-d2bf-44f1-a88b-7dc704bfe682  none                     swap     sw                   0  0  


/dev/sdc1                                  /media/sdc1              vfat     owner,users,user     0  0  

im running ubuntu 10.10 eeepc 1015pn

---

### Post by hawkmage on 2011-02-07
With the sd card inserted and with out it what do you get from the command:
```
sudo blkid
```

---

### Post by eats7 on 2011-02-07
Inserted: 


/dev/sda1: UUID="A2825FFB825FD281" TYPE="ntfs" 
/dev/sda2: UUID="3c014022-8567-40c6-9aef-5dd1d6e135ed" TYPE="ext4" 
/dev/sda5: UUID="741efd93-d2bf-44f1-a88b-7dc704bfe682" TYPE="swap" 
/dev/sdb1: LABEL="PENDRIVE" UUID="64D1-D238" TYPE="vfat" 

Not Insterted:

/dev/sda1: UUID="A2825FFB825FD281" TYPE="ntfs" 
/dev/sda2: UUID="3c014022-8567-40c6-9aef-5dd1d6e135ed" TYPE="ext4" 
/dev/sda5: UUID="741efd93-d2bf-44f1-a88b-7dc704bfe682" TYPE="swap"

---

### Post by hawkmage on 2011-02-07
That would indicate that the system is seeing the removable media and your internal NTFS drive as separate devices.  Do you have a somehitn special in the /etc/auto_* files for the automounter?

Also what do you get if you run the mount command to list the mounts with the removable media in and out?

---

