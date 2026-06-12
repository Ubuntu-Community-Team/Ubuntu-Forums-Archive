---
title: "Interrupted copy now can't unmount"
date: 2010-02-09
forum: General Help
---

### Post by andreselsuave on 2010-02-09
Hi there!

I use Kubuntu Karmic, and I was copying some stuff from one partition to other, and the target partition filled up, so the copy wasn't finished. Now I cant unmount the drive.

```
andreselsuave@sobremesaup:~$ sudo umount -f /dev/sda1
[sudo] password for andreselsuave:
umount: /home/dad: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

```

looks like the copying process is still there (even after reboot) and lock the drive. 

thanks in advance

---

### Post by andreselsuave on 2010-02-09
Nevermind a second reboot did the job

---

