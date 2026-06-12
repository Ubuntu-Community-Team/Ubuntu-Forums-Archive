---
title: "To dual boot with Wubi, or how I have for a while"
date: 2011-04-24
forum: General Help
---

### Post by CTrance on 2011-04-24
Well I've been using linux on a desktop with my family for half a year now dual booting XP and linux mint. I simply partitioned the hard drive since I had no idea about this wonderful thing called wubi that a friend informed me of today.

I want to install Ubuntu on my laptop now, and I'm going to be dual booting windows 7 with it. Now I know I can partition things properly, as I have done it several times before. And I don't plan on upgrading until 11.10, which will be in 6 months when I'll want to reformat anyway. And I know I love linux, so I don't plan to use the 'uninstall' feature of wubi...

Should I go with a Wubi install or should I just go with installing it from a live USB drive as I always have?

What are the pros and cons of each process?

Thanks in advance guys, all input is appreciated!

---

### Post by maverick555 on 2011-04-24
with wubi you still using ntfs or fat file system which is slow comparing to ext4. Apart from that i don't think anything else to consider.I would personally recommend using wubi if you are planning on formating in coming days.

---

### Post by Rubi1200 on 2011-04-24
If you know you plan on using Ubuntu, it is probably best to install to the drive.

Just make sure you backup all important data first, prepare the partitions in advance, and use manual partitioning for finer control of the process when you start the installer.

Here is a great guide to start reading:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

By the way, off-topic a bit, but this:
> with wubi you still using ntfs or fat file system
is simply incorrect.

Wubi uses a loop-mounted virtual disk to install Ubuntu. Once Ubuntu is selected from the boot menu, it uses the ext4 file-system, which is the current default for Ubuntu since version 9.10.

---

