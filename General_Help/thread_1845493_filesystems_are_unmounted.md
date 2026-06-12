---
title: "filesystems are unmounted"
date: 2011-09-17
forum: General Help
---

### Post by shubham1 on 2011-09-17
the filesystems are unmounted by default.
i have the folowing filesystems
105gb filesystem
workspace
file system
105gb file system and workspace are unmounted by defalut when i open my desktop
when i try open files before unmounting them throught hugs it syas cant open wehn i click on that partion then is mounted
wehn ever i open rythmbox musicplayer it cant open files it shows them as missing files then i got its not the problem of rythmbox the 105gbfilesystem is unmounted so it cant get the files banshee loads but cant play how to mount them by defalut

---

### Post by dino99 on 2011-09-17
sudo dpkg-reconfigure mountall

---

### Post by shubham1 on 2011-09-17
> **dino99 said:**
> sudo dpkg-reconfigure mountall
i did it i will check whether it works or not when i will shutdown

---

### Post by Morbius1 on 2011-09-17
And when that doesn't work please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```And tell us which one of the partitions in the "blkid" listing is the "105gb filesystem" and the "workspace"

---

### Post by shubham1 on 2011-09-17
> **Morbius1 said:**
> And when that doesn't work please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```And tell us which one of the partitions in the "blkid" listing is the "105gb filesystem" and the "workspace"
ok if it does not works i will post the output

---

### Post by shubham1 on 2011-09-18
> **Morbius1 said:**
> And when that doesn't work please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```And tell us which one of the partitions in the "blkid" listing is the "105gb filesystem" and the "workspace"
/dev/sda1: LABEL="workspace" UUID="6FD05ABF269DE8CD" TYPE="ntfs" 
/dev/sda2: UUID="F6A0F4D2A0F49A77" TYPE="ntfs" 
/dev/sda4: UUID="df24db11-600a-4c92-a742-d1adce04a4e9" TYPE="ext4" 
/dev/sda5: UUID="41c62031-3369-4976-8f1e-c67daddbb233" TYPE="swap"

---

### Post by shubham1 on 2011-09-18
> **Morbius1 said:**
> And when that doesn't work please post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```And tell us which one of the partitions in the "blkid" listing is the "105gb filesystem" and the "workspace"
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=df24db11-600a-4c92-a742-d1adce04a4e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=41c62031-3369-4976-8f1e-c67daddbb233 none            swap    sw              0       0

---

### Post by shubham1 on 2011-09-18
> **shubham1 said:**
> ok if it does not works i will post the output
/dev/sda4 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shubham/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shubham)

---

### Post by Morbius1 on 2011-09-18
If you have manually mounted these partitions since your last post unmount them. Then follow these steps:[B]

[1] Create permanent homes for your new partitions:[/B]
```
sudo mkdir /media/Workspace
``````
sudo mkdir /media/Data
```[B]
[2] Edit /etc/fstab as root:[/B]
```
gksu gedit /etc/fstab
```**[3] Add the following lines to the end of fstab:**
```
UUID=6FD05ABF269DE8CD /media/Workspace ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
``````
UUID=F6A0F4D2A0F49A77 /media/Data ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
```**[4] Save fstab, exit gedit, and back in the terminal run the following command which will test for errors and if none will mount the new partitions without a reboot:**
```
sudo mount -a
```

---

### Post by shubham1 on 2011-09-19
> **Morbius1 said:**
> If you have manually mounted these partitions since your last post unmount them. Then follow these steps:[B]

[1] Create permanent homes for your new partitions:[/B]
```
sudo mkdir /media/Workspace
``````
sudo mkdir /media/Data
```[B]
[2] Edit /etc/fstab as root:[/B]
```
gksu gedit /etc/fstab
```**[3] Add the following lines to the end of fstab:**
```
UUID=6FD05ABF269DE8CD /media/Workspace ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
``````
UUID=F6A0F4D2A0F49A77 /media/Data ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
```**[4] Save fstab, exit gedit, and back in the terminal run the following command which will test for errors and if none will mount the new partitions without a reboot:**
```
sudo mount -a
```
errors:
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

---

### Post by raja.genupula on 2011-09-19
[http://ubuntuforums.org/showthread.php?t=1568372](http://ubuntuforums.org/showthread.php?t=1568372)

look at this

---

### Post by shubham1 on 2011-09-19
my porblem is not the boot see the thread
showthread.php?p=11265278

---

### Post by Morbius1 on 2011-09-19
post the output of the following commands please:
```
mount
```
```
cat /etc/fstab
```

---

### Post by shubham1 on 2011-09-20
> **Morbius1 said:**
> post the output of the following commands please:
```
mount
```
```
cat /etc/fstab
```
mount:
/dev/sda4 on / type ext4 (rw,errors=remount-ro,commit=0)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shubham/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shubham)
/dev/sda1 on /media/workspace type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/F6A0F4D2A0F49A77 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by shubham1 on 2011-09-20
> **Morbius1 said:**
> post the output of the following commands please:
```
mount
```
```
cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=df24db11-600a-4c92-a742-d1adce04a4e9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=41c62031-3369-4976-8f1e-c67daddbb233 none            swap    sw              0       0
UUID=6FD05ABF269DE8CD /media/Workspace ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
UUID=F6A0F4D2A0F49A77 /media/Data ntfs defaults,nls=utf8,uid=1000,umask=000 0 0

---

### Post by shubham1 on 2011-09-20
thanks it work but the location is changed when i ryhtm box it redistered them as missing files but now i imported again.

---

### Post by shubham1 on 2011-09-20
bacuse of this my other thread is solved
[http://ubuntuforums.org/showthread.php?p=11268296#post11268296](http://ubuntuforums.org/showthread.php?p=11268296#post11268296)
my three threads has sloved together 2 of you and one of shut down

---

### Post by Morbius1 on 2011-09-20
I did not understand your last 2 posts.

Your fstab entries are correct:
> UUID=6FD05ABF269DE8CD /media/Workspace ntfs defaults,nls=utf8,uid=1000,umask=000 0 0
UUID=F6A0F4D2A0F49A77 /media/Data ntfs defaults,nls=utf8,uid=1000,umask=000 0 0     Since they are not mounting at your specified mount points:
> mount:
[COLOR=Blue]/dev/sda1 on /media/workspace[/COLOR] type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions)
[COLOR=Blue]/dev/sda2 on /media/F6A0F4D2A0F49A77[/COLOR] type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_ permissions) I'm going to guess that you did not follow the first 2 items of my post:
> If you have manually mounted these partitions since your last post unmount them. Then follow these steps:[B]

[1] Create permanent homes for your new partitions:[/B]
     Code:
     sudo mkdir /media/Workspace 
     Code:
     sudo mkdir /media/Data 


---

### Post by shubham1 on 2011-09-20
i did it it says file exits that means i did it and now it is by default when i opened my system

---

