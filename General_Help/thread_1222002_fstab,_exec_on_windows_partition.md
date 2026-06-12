---
title: "fstab, exec on windows partition"
date: 2009-07-24
forum: General Help
---

### Post by bender1234 on 2009-07-24
Hey I'm trying to mount a windows drive with all permissions at bootup.

I've added the following line to /etc/fstab
/dev/sda3    /mnt/drive_d    ntfs-3g    auto,exec,async,users,utf8,uid=stian 0 0

however I don't get the permission to execute files, everything else works fine. What's wrong with
the above line? Mounting it manually works like a charm though, but I want to do it the proper way.

permissions say -rwxrwxrwx.
But even as root I cannot execute files. 
(Want to mount my projects dir on windows disk so I can have all my source code in the same dir structure,
and avaliable from both win 7 and linux)

...
-rwxrwxrwx 1 root root  3696 2009-07-24 04:15 PlaybackWidget.o
-rwxrwxrwx 1 root root 46369 2009-07-24 04:25 qcam
stian@stian-laptop:~/Projects/linux/qt/qtcam$ ./qcam
bash: ./qcam: Permission denied


cheers

---

### Post by bender1234 on 2009-07-24
bump :)

I'm sure there must be a way to make this work, anyone please?

Don't want to have to go to bash and do this for each time I boot

stian@stian-laptop:~$ sudo mount /dev/sda3 /mnt/drive_d
[sudo] password for stian: 
stian@stian-laptop:~$

---

### Post by TeoBigusGeekus on 2009-07-24
> **bender1234 said:**
> 
/dev/sda3    /mnt/drive_d    ntfs-3g    auto,exec,async,users,utf8,uid=stian 0 0

If you changed this line to

```
/dev/sda3    /mnt/drive_d    ntfs-3g    relatime 0 0
```

perhaps?

---

### Post by bender1234 on 2009-07-24
Sweet thanks a bunch, worked like a charm :)

---

