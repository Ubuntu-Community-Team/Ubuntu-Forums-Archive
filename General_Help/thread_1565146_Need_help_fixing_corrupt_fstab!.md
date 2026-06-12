---
title: "Need help fixing corrupt fstab!"
date: 2010-08-31
forum: General Help
---

### Post by fr0sty on 2010-08-31
hello, I recently tried to mount my windows partition in ubuntu via use with the ntfs-3g tool and didnt specify the mountpoint myself. After a reboot, i realized that the ntfs-3g tool had made my windows mountpoint "/" which is the same as the root filesystem. I am no longer able to boot to ubuntu because of this. What I need to do is edit my /etc/fstab so that it has the proper mount name. Here are my partitions:
- /dev/sda1 is * 
- /dev/sda2 is Windows 7
- /dev/sda3 is Ubuntu 10.04
- /dev/sda4 is the linux swap.

here is my fstab file:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>   <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
/dev/sda2        /       ntfs    defaults,nls=utf8,umask=0222 0  0
/dev/sdb1        /media/TheGoodStuff   ntfs-3g defaults,nosuid,nodev,locale=en_US.utf8  0  0
/dev/sda1        none    swap    sw   0   0

If you have any idea how i can fix the fstab to have my ubuntu in it and how to rename the windows mount point, id be very happy... i am using nano from commandline to get this info.

---

### Post by Elfy on 2010-08-31
Try this, run

```
blkid
```

to get the UUID then in fstab

```
UUID=longnumberfromblkid /  ext4  errors=remount-ro 0 1
```

if you can't get the uuid 

```
/dev/sda3 /  ext4  errors=remount-ro 0 1
```

Though it is possible you have a backup 

```
ls /etc/fstab*
```to search

---

### Post by 3Miro on 2010-08-31
The best way is probably to get an Ubuntu LiveCD and then boot from that. You should be able to use Linux and more easily edit files.

If you can get to the fstab from command line, then you need to go for:

```
sudo nano /etc/fstab
```

and then comment the Windows 7 line (add a # in front of it) and then add a line that looks like:

```
 /dev/sda3  /  ext4    errors=remount-ro  0  1 
```

Basically your new file should look like:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <pass>

proc /proc proc nodev,noexec,nosuid 0 0
#/dev/sda2 / ntfs defaults,nls=utf8,umask=0222 0 0
/dev/sda3  /  ext4    errors=remount-ro  0  1 
/dev/sdb1 /media/TheGoodStuff ntfs-3g defaults,nosuid,nodev,locale=en_US.utf8 0 0
/dev/sda1 none swap sw 0 0

```

---

### Post by fr0sty on 2010-08-31
i am unable to save my changes in nano when editing /etc/fstab: read-only file system... how do i save changes?

---

### Post by Elfy on 2010-08-31
run as root 

sudo nano /etc/fstab

Where are you trying to do this?

if you are in a livecd then you will need to mount the partition before you can get to the file.

Edit - so possibly in a livecd 

sudo mkdir /mnt/temp
sudo mount -t ext4 /dev/sda3 /mnt/temp
sudo nano /mnt/temp/etc/fstab

---

### Post by 3Miro on 2010-08-31
"read only file system" means you will probably have to use a live CD. sudo will not help you save files if they are "mounted read only".

---

### Post by fr0sty on 2010-08-31
sorry for so many questions... but I type "sudo nano /etc/fstab" but when it loads, it says at the bottom "Read 11 lines (Warning: No write permission)"... and when I save, it says it is a read-only file system

---

### Post by fr0sty on 2010-08-31
hold up, let me try from cd... good idea

---

### Post by fr0sty on 2010-08-31
um... what do i need to do to get to the point where I can edit the fstab on the hdd... once again thanks in advance.

---

### Post by Rubi1200 on 2010-08-31
See the reply from forestpiskie above.

---

### Post by fr0sty on 2010-08-31
I got it. THANK YOU SOOOO MUCH! I thought I had lost all my school work! thanks sooo much again!

---

### Post by Elfy on 2010-08-31
welcome - boot first to make sure though :)

Then invest some time in a backup ...

---

### Post by 3Miro on 2010-08-31
Backup is a good idea, also keeping a LiveCD handy for just this kind of situations. Unless data gets erased from the hard drive, the CD can recover it.

---

### Post by Rubi1200 on 2010-08-31
Glad you got it sorted out :D

---

