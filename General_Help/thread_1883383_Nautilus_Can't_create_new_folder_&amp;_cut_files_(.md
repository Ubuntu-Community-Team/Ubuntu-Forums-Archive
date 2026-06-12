---
title: "Nautilus: Can't create new folder &amp; cut files (Ctrl+X) in NTFS filesystem"
date: 2011-11-19
forum: General Help
---

### Post by onizuka45 on 2011-11-19
I want to create a folder in partition D, which is NTFS filesystem, but why I can't create new folder or even cut files (Ctrl+X) in NTFS filesystem? I'm using Ubuntu 11.10.

[ATTACH]207540[/ATTACH]

[ATTACH]207543[/ATTACH]

---

### Post by mikewhatever on 2011-11-19
That looks a lot like the problem with ownership. When a certain user doesn't own the file system, it will only have read access. How did you mount that partition? Can you post the output of the **mount | grep ^/** command.

---

### Post by onizuka45 on 2011-11-19
You mean, type **"mount"** on terminal or...

---

### Post by mikewhatever on 2011-11-19
Yes, type 'mount', hit 'Enter', and post the resulting output.

... **mount | grep ^/** would be even better.

The output will just show all mounted partitions.

---

### Post by raja.genupula on 2011-11-19
Hi man 
When you have installed Ubuntu ?  from what time you're facing this problem ? 
why i am asking means I am also faced the same problem and nothing worked for me.

At that time i am using dev release of Xubuntu and suddenly one day i am unable to save anything on my drives(NTFS) , i have waited for a while and after some days may be hardly 2-3 its solved automatically still i dont know why i have got that but 

what i wanna suggest is please keep updating your system and in a while it will be solved.
Here is my thread Link......
may be it will helpful to you for a while 
[http://ubuntuforums.org/showthread.php?t=1867880](http://ubuntuforums.org/showthread.php?t=1867880)

---

### Post by onizuka45 on 2011-11-19
Here's my output:

/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/acer/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=acer)
/dev/sr0 on /media/ZTEMODEM type iso9660 (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,mode=0400,dmode=0500,uhelper=udisks)
/dev/sda1 on /media/ACER type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)
/dev/sda3 on /media/DATA type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)

---

### Post by mikewhatever on 2011-11-19
Thanks for the output. The relevant part seems to be this:
```

/dev/sda1 on /media/ACER type ntfs (**ro**,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmas k=0177,uhelper=udisks)
/dev/sda3 on /media/DATA type ntfs (**ro**,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmas k=0177,uhelper=udisks)

```

As you can see, both partitions are mounted as read only (ro).

Apparently, the problem is not with ownership, so I suspect unclean filesystems.
Can you post the output of **dmesg | grep -e sda1 -e sda3** as well.

---

### Post by onizuka45 on 2011-12-03
You mean, this: [    2.229264]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 > sda3.

---

### Post by fdrake on 2011-12-03
this should fix it. [http://ubuntuforums.org/showthread.php?t=1883686](http://ubuntuforums.org/showthread.php?t=1883686)

make sure when you rebbot that you /etc/fstab(if you have saved it before) says mount with type "fuseblk" and not ntfs!
or just do:
```

sudo mkdir /media/ACER
sudo mount -t fuseblk /dev/sda1 /media/ACER

```

---

### Post by Morbius1 on 2011-12-03
>  /dev/sda1 on /media/ACER type ntfs (ro,nosuid,nodev,uid=1000,gid=1000,dmask=0077,fmask=0177,uhelper=udisks)Something doesn't make sense about that output from "mount". If you mount it through Nautilus it wouldn't show up like that so I'm guessing you have an entry in fstab that's telling it to do that. 

Please post the output of the following command please:
```
cat /etc/fstab
```

---

