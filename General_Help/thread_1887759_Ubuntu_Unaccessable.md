---
title: "Ubuntu Unaccessable"
date: 2011-11-27
forum: General Help
---

### Post by Shvesley on 2011-11-27
I was using Ubuntu 11.10 as normal when suddenly my computer turned off. So, I turned it on and booted my 11.10 partition again as I usually do. I was met with a blank purple screen. When I tried again I had a black screen with the little flashing white mark in the corner. I booted into my XP partition and installed Wubi because I read that you could access your Ubuntu files from Windows that way. So, I do that, but I cannot mount my 11.10 partition in Wubi I get the following error...

Unable to mount 105 GB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is going on?! I have many important files on my Ubuntu partition and I need them for school. Also, I did just run some Minecraft Server software before this happened, but it was all closed when the "crash" occurred. I really need some help here.

---

### Post by oldtimer7777 on 2011-11-27
Create a Live Bootable USB Flash Drive of Ubuntu from the Ubuntu.com web site.  Or create a live disc of Ubuntu and boot from that.  You should be able to access it at that point. Don't use Wubi to repair your partitions either.

> **Shvesley said:**
> I was using Ubuntu 11.10 as normal when suddenly my computer turned off. So, I turned it on and booted my 11.10 partition again as I usually do. I was met with a blank purple screen. When I tried again I had a black screen with the little flashing white mark in the corner. I booted into my XP partition and installed Wubi because I read that you could access your Ubuntu files from Windows that way. So, I do that, but I cannot mount my 11.10 partition in Wubi I get the following error...

Unable to mount 105 GB Filesystem

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What is going on?! I have many important files on my Ubuntu partition and I need them for school. Also, I did just run some Minecraft Server software before this happened, but it was all closed when the "crash" occurred. I really need some help here.

---

### Post by Shvesley on 2011-11-27
OK. I have plenty of those lying around. Also, how do  fix the problem? Is it repairable? What happened you think?

---

### Post by Shvesley on 2011-11-27
It did not work. I booted from a USB and I still get the same error when I try to mount

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by oldtimer7777 on 2011-11-27
> **Shvesley said:**
> It did not work. I booted from a USB and I still get the same error when I try to mount

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

You are going to have to hang in there until someone else who knows how to fix this can take a look.

---

### Post by Shvesley on 2011-11-27
[LEFT]Ok. Message me if you find anything. Thanks a ton man, I don't know what I would have done without you.
[/LEFT]

---

### Post by bcbc on 2011-11-28
Likely there was some file system corruption when the computer shutdown. Try fsck'ing your partition:
```
sudo fsck /dev/sda1
```

You can do this from either a live CD/USB or Wubi. It makes no difference.

---

### Post by Shvesley on 2011-11-28
Ok, I will try that.

---

### Post by Shvesley on 2011-11-28
The output was:

fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
/dev/sda1: clean, 304187/6406144 files, 11963742/25600000 blocks

---

### Post by bcbc on 2011-11-28
Add some options (f - force, v - verbose output):
```
sudo fsck -fv /dev/sda1
```

You can also add the option -y (or -fyv) to "assume "yes" to all questions". Without that you'll be prompted on how to repair corrupted files.

---

### Post by Shvesley on 2011-11-29
FIXED!

[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

This article was a life saver. Thanks so much guys!

---

### Post by bcbc on 2011-11-29
> **Shvesley said:**
> FIXED!

[http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/](http://www.cyberciti.biz/faq/recover-bad-superblock-from-corrupted-partition/)

This article was a life saver. Thanks so much guys!
Cool - that's a nice guide!

---

### Post by Shvesley on 2011-11-30
Yes, it was. The output was a little scary at first. There were a lot of numbers scrolling across the screen for a while, but it was all part of the process.

---

