---
title: "Trying to zero fill sda"
date: 2010-09-12
forum: General Help
---

### Post by saibott on 2010-09-12
Hey! I hope someone can help me. I'm trying to zero fill my HD and reinstall ubuntu to extend the HD's lifetime for a bit. This is because I have been starting getting bad sectors and the computer now keeps freezing all the time and most programs wont even start. I know the HD is a dead man walking but I need some more time. 
I have unmunted the drive and are runing from liveCD but when I try to run dd if=/dev/zero of=/dev/sda in terminal nothing happens, and I mean nothing. why is this??

---

### Post by saibott on 2010-09-12
ok, maybe I was abit fast, something DID eventually happen After trying a couple of time I now get this message: 
ubuntu@ubuntu:~$ sudo dd if=/dev/zero of=/dev/sda
dd: writing to `/dev/sda': Input/output error
17545513+0 records in
17545512+0 records out
8983302144 bytes (9,0 GB) copied, 1805,04 s, 5,0 MB/s

wtf??
Enybody know if there is a way to force this?

---

### Post by coffeecat on 2010-09-12
Two points:

I don't think zeroing a drive will deal with bad sectors. If the HD really is a 'dead man walking' back out now. Get rid of it. Don't entrust any of your data or precious time and energy to it. It's not worth it.

But if you really want to zero the drive, you might find shred more helpful. From the live CD terminal:

```
sudo shred -zvn 0 /dev/sda
```The -n 0 option tells it to shred with zero number of passes, and the -z option tells it to zero the drive **after** it's shredded it which means, in the dumb logical way of computers, it will simply zero the drive in one pass. The -v option gives you a little bit of output to reassure you that something is really happening.

---

### Post by HermanAB on 2010-09-12
Howdy,

Chuck the disk away.  Disks never get better.

Note that you can also use cat:
$ sudo cat /dev/zero>/dev/sda

---

### Post by dcstar on 2010-09-13
> **coffeecat said:**
> Two points:

I don't think zeroing a drive will deal with bad sectors.


Correct, this is not 1985 where you still "formatted" hard disks. The low-level formatting is done in the factory and there is **nothing** a user can do to fix problems with bad blocks apart from running scans in a partition to let the OS mark the blocks as not to be used.

---

