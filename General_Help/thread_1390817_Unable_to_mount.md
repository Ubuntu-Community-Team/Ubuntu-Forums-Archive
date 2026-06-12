---
title: "Unable to mount"
date: 2010-01-26
forum: General Help
---

### Post by surojeetdey on 2010-01-26
Hello,

This is first post here ............. :KS

I have installed UBUNTU on my LAPTOP and now I am not able to access any other NTFS partation

sudey@ubuntu:~$ cat /etc/fstab
UUID=3AB079A2B07964F3 /media/3AB079A2B07964F3 ntfs-3g defaults 0 0
UUID=2A107E38107E0AD9 /media/VOLT ntfs-3g remount 0 1
UUID=0AE0F0F6E0F0E8B9 /media ntfs-3g remount 1 0
UUID=A2B86856B8682B4D /host ntfs-3g defaults 0 0

sudey@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda7 /media/VOLT
[sudo] password for sudey: 
fuse: failed to access mountpoint /media/VOLT: No such file or directory
sudey@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda7 /media/VOLT -o force
fuse: failed to access mountpoint /media/VOLT: No such file or directory
sudey@ubuntu:~$ mount -a
mount: only root can do that
sudey@ubuntu:~$ sudo mount -a
fuse: failed to access mountpoint /media/3AB079A2B07964F3: No such file or directory
Remounting is not supported at present. You have to umount volume and then mount it once again.
Remounting is not supported at present. You have to umount volume and then mount it once again.

I am not getting what went wrong but I need to access 2 NTFS partition  and I am not able to do --- suggest me

---

### Post by byStanderone on 2010-01-26
...had seen this thread, i hope if fits to what you need:
[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by rnerwein on 2010-01-26
hi
i ain't know if your problem is already fixed - if not would be nice to post the output of: fdisk -l /dev/sdX (X = disk a ?).
my looks like this:
/dev/sda3           46484       58566    97046524    7  HPFS/NTFS
and fstab is:
/dev/sda3 /vista_data ntfs defaults,noauto,umask=777

i just type in the terminal:# mount /vista_data    (be sure you create the mount point before)
and it works fine for me !
ciao

---

### Post by cayliffe on 2010-01-26
Before you try and mount the partition does the directory "/media/VOLT" exist?

The mount point must exist before you actually try and mount a file system on it.

Craig

---

### Post by surojeetdey on 2010-01-26
Thanks GUYS for the help :D ...................

IT worked after creating the directory 

sudey@ubuntu:~$ sudo mkdir /media/VOLT
[sudo] password for sudey: 
sudey@ubuntu:~$ chmod -777 /media/VOLT
chmod: invalid option -- '7'
Try `chmod --help' for more information.
sudey@ubuntu:~$ man chmod
sudey@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda7 /media/VOLT
sudey@ubuntu:~$ sudo mkdir /media/WIPRO
sudey@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda5 /media/WIPRO
sudey@ubuntu:~$

---

### Post by jamesisin on 2010-01-26
You can bookmark this for future reference:

[http://www.soundunreason.com/InkWell/?p=587](http://www.soundunreason.com/InkWell/?p=587)

---

