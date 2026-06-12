---
title: "no space on device"
date: 2011-01-17
forum: General Help
---

### Post by xiahn on 2011-01-17
Hi everyone, 
I'm new to the ubuntu. I kept encountering the error that "no space on device".

I used the "df" command and it showed:
[I]
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/loop0             2765720   2719592         0 100% /
none                   1019616       316   1019300   1% /dev
none                   1024344       300   1024044   1% /dev/shm
none                   1024344        88   1024256   1% /var/run
none                   1024344         0   1024344   0% /var/lock
none                   1024344         0   1024344   0% /lib/init/rw
/dev/sda3             74207224  54591024  19616200  74% /host
/dev/sda6             25461756  23309676   2152080  92% /media/After Work
/dev/sda5             46051320  42427268   3624052  93% /media/Courses & Research[/I]

The /dev/loop0 doesn't seem to be a directory, so I don't know what to do get some extra space. Any help will be appreciated! 

Thanks a lot,
Henry

---

### Post by v1nny on 2011-01-17
> **xiahn said:**
> 
/dev/loop0             2765720   2719592         0 100% /


For some reason your root ("/") is mounted on a loop back device that is only about 2GB. Are you running off some kind of live cd/usb? If not, did you do any strange configuration during your install?

Typically you should see root mounted to hard drive partition (such as /dev/sda1).

What is the output from:
> losetup -a

---

