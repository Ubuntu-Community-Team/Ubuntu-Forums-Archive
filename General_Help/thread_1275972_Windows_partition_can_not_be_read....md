---
title: "Windows partition can not be read..."
date: 2009-09-26
forum: General Help
---

### Post by Chrisname on 2009-09-26
I got an error when booting into Ubuntu today. Like an idiot I forgot to write down what the error was, but I decided it might be fixed by reinstalling Ubuntu. Again like an idiot, I deleted my Ubuntu partition from within windows (I like the partitioner) which contains the menu.lst file. After booting my Ubuntu CD (lucky I still have it, I lent it to a friend... good thing he gave it back :P) and reinstalling, I tried to boot into windows (my family all use it, and it's where I put all of my old Ubuntu files as backups). Windows threw some errors at me, so I booted into Ubuntu to see if I could fix it from there. It was then that my stomach dropped and I realised I couldn't mount my windows partition -- Ubuntu hadn't even recognised it. So I apt-get'd gparted to see if that could help me.

The following is a screenshot of gparted:
[http://i35.tinypic.com/2a94l7n.png](http://i35.tinypic.com/2a94l7n.png)
I posted a link because it's probably too big to embed.

/dev/sda2 is my windows partition. As you can see gparted is claiming not to be able to read it. The same for /dev/sda1 which is meant to be a boot partition for windows or something. The 65GB is where I was going to install Ubuntu, but I didn't get the option to, so I installed it to the 9GB partition instead (which is where I was probably going to install FreeBSD or something).

I installed Jaunty to /dev/sda3 using the "Specify partitions manually" option because the "side by side" option with the slider bar thing didn't appear. I would have used that and probably wouldn't be posting this message, but there you go... I specified the /dev/sda3 partition as ext3 to be used as "/" and didn't allocate swap space because this is just a temporary installation.

This windows partition (the 520GB one) has alot (almost 200GB) of personal stuff on it of my family, and, currently, myself (although I only have it on there because I was planning to reinstall Ubuntu).

Anyway, does anyone know what I did to antagonise my windows partition, and how I can fix it? Thank you.


My life will be so much simpler when I get my own computer... Only £336/£336 left to earn :P

---

### Post by StuartN on 2009-09-26
> **Chrisname said:**
> I tried to boot into windows (my family all use it, and it's where I put all of my old Ubuntu files as backups). Windows threw some errors at me, 

Well that is a good sign - if Windows threw an error at you, then Windows booted (it just did not complete). You would need some kind of Windows recovery disk.

---

### Post by Chrisname on 2009-09-26
> **StuartN said:**
> Well that is a good sign - if Windows threw an error at you, then Windows booted (it just did not complete). You would need some kind of Windows recovery disk.
The error it threw was something to do with booting, and then it said something about an installer. I have a recovery disk somewhere, I'll try it in a minute.

---

### Post by Chrisname on 2009-09-27
I'm not sure what to do here. I have a couple of recovery CDs here but they're for resetting the hard disk and reinstalling windows, which will wipe the hard disk I think.

I tried using ```
mount -t ntfs /dev/sda2 /media/vista
```; but it didn't work. I need to get the contents of the partition so that I can back it up, then I can wipe the disk and reinstall windows and Ubuntu.

Below is the command and information from mount...

> $ sudo mount -t ntfs /dev/sda2 /media/vista
----
Unexpected clusters per mft record (-1).
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

[b][u]Never mind now, the recovery CD worked.
Thanks.[/u][/b]

---

### Post by StuartN on 2009-09-27
> **Chrisname said:**
> **_Never mind now, the recovery CD worked. Thanks._**

Can you just post what you did with your Windows CD for anyone else who discovers this thread.

---

