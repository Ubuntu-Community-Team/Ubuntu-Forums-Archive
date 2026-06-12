---
title: "mounting file system problems in 11.10"
date: 2012-03-15
forum: General Help
---

### Post by nashtrik on 2012-03-15
I am a completely new user of Ubuntu/Linux...I installed version 11.10 recently...the problem is...when i login with my administrative account,it does not mount the file systems,it does detect the USB flash drive but doesn't mount it...unable to mount,not authorized is the message..whereas..when i log in with a guest session,it mounts all the file systems,flash drive...everything...where is the problem...? Any solutions....?Also,I am unable to shut down the system from admin. account. Even with the guest session,shut down dowsn't work,I have to Hibernate..

PS:- initially it did mount all the file systems from the administrative account,but once the system was shut down from the power source without proper logout/shut down...the problem seems to have crept after this...might this be the plausible reason...?

---

### Post by MSPdwalt on 2012-03-15
I'm assuming you've tried un-plugging and plugging the device back in after logon has finished?

What filesystems are on the drive(s) you're trying to access?  They're not encrypted or anything are they?

After you plug/unplug the devices post the output of

```
dmesg
```

---

### Post by MSPdwalt on 2012-03-15
When you say "My administrative user" are you revering to the user you created at install?

If you created another user after install and that's the problem one, go to System > Administration > Users & Groups.  Click your problem user and choose advanced settings.

[IMG]http://img845.imageshack.us/img845/1580/selection008o.png[/IMG]

---

### Post by nashtrik on 2012-03-15
I have four partitions on my hard drive...I have windows XP and ubuntu installed on the first partition...all are NTFS...I had encrypted my home folder while installing ubuntu...Like..I wanted to change the desktop background with a family picture which was on the other partition ,but when i double clicked on that partition ,the error "unable to mount file system,not authorized" crept up....but when i changed my session to guest session,it mounted all the drives,i successfully changed my desktop background,was able to transfer a document to USB flash drive...
                                                                    I hope ,I have made it clearer,pardon me,this is a totally unexplored territory for me....!!!

---

### Post by nashtrik on 2012-03-15
Unfortunately,the administrative account which i created during install is the problem area...I did not create any other account....

---

