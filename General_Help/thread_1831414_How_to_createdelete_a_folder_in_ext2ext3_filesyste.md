---
title: "How to create/delete a folder in ext2/ext3 filesystem...??"
date: 2011-08-23
forum: General Help
---

### Post by Sufi.DU on 2011-08-23
I have created a new partition in ubuntu 11.04 using GParted partition manager. The file system of the new partition is ext3. But the problem is, I can't create any folder in my new partition. The option to create a folder is showing disable. How can I create/delete folder in my new ext3 filesystem partition. Can anyone help me? Please it is urgent.


Thanks.

---

### Post by mikewhatever on 2011-08-23
There is no secret trick in creating folders in the ext3 file system. As with all other file systems, it should be mounted as read/write. How did you mount the partition?

---

### Post by raja.genupula on 2011-08-23
you have created the partition . i have got this from a thread sounds it will be useful to you 
If you only use the machine, I mean only one user is there on the machine, I would suggest you to own the partition and give permissions to read and execute to the others, by doing:
 
sudo chown /media/<name of the partition> -R ; sudo chmod 755 /media/<name of the partition> -R
If you have more than one user on your machine and you want to share the partition with everyone permitting each one to do read, write and execute on this partition, you may do:
 
sudo chmod 777 /media/<name of the partition> -R

---

### Post by aeiah on 2011-08-23
your user account probably just doesn't have permission to write to it. does it work using sudo?

---

### Post by Sufi.DU on 2011-08-23
> **mikewhatever said:**
> There is no secret trick in creating folders in the ext3 file system. As with all other file systems, it should be mounted as read/write. How did you mount the partition?


I am just using GParted to create a new partition & does not mention any mount point. How can I use it?

Thnx for reply.



> **raja.genupula]you have created the partition . i have got this from a thread sounds it will be useful to you 
If you only use the machine, I mean only one user is there on the  machine, I would suggest you to own the partition and give permissions  to read and execute to the others, by doing:
 
sudo chown /media/<name of the partition> -R  said:**
> 

What do you mean by name of the partition? Is this is the partition number? Such as '/dev/sda9' 

Thnx for reply



[QUOTE=aeiah]your user account probably just doesn't have permission to write to it. does it work using sudo?

Yes, sudo is working on my machine. How can I achieve write permission..??

Thnx for reply

---

### Post by Morbius1 on 2011-08-23
Please post the output of the following command and tell us which partition is the new one:
```
mount
```

---

### Post by paxxus on 2011-08-23
Did you format the partition? I seem to recall that you should use "Partition-> New" and then "Partition -> Format to".

---

### Post by muctadir on 2011-08-23
You can use the command below.
```
sudo nautilus
```
This will open a file browser with root access. Now, check if you can do your desired tasks.

---

### Post by Sufi.DU on 2011-08-24
> **Morbius1 said:**
> Please post the output of the following command and tell us which partition is the new one:
```
mount
```


sufi@Sufi-DU:~$ mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda6 on /boot type ext3 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sufi/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sufi)
/dev/sda10 on /media/Software type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda8 on /media/Documents type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb1 on /media/SAGAR type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sda9 on /media/79a7cd80-cc74-486c-af8c-2a50c823d1a9 type ext3 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda12 on /media/Video-1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda11 on /media/Audio type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda13 on /media/Video-2 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)



Here /dev/sda9 is my new partition which is in ext3 format.



[QUOTE=paxxus]Did you format the partition? I seem to recall that you should use "Partition-> New" and then "Partition -> Format to". [/QUOTE]

I have format it in ext3 form.

---

### Post by Sufi.DU on 2011-08-24
> **muctadir said:**
> You can use the command below.
```
sudo nautilus
```This will open a file browser with root access. Now, check if you can do your desired tasks.


Yes, I tried this command. But it needs every time when I perform any task on that partition. I think this is little bit disgusting to run this command every time. Do you know any simple task to avoid this?

---

### Post by tredegar on 2011-08-24
Mount the partition, then
**sudo chmod 777 /media/79a7cd80-cc74-486c-af8c-2a50c823d1a9**
Then anyone can read/write from/to it.

---

### Post by Sufi.DU on 2011-08-24
> **tredegar said:**
> Mount the partition, then
**sudo chmod 777 /media/79a7cd80-cc74-486c-af8c-2a50c823d1a9**
Then anyone can read/write from/to it.


I am tried, but nothing was happen. I can't create any folder. The option is also disable. I am frustrate :( :confused:

---

