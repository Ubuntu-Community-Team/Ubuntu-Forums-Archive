---
title: "Mounting Externel Drives"
date: 2010-10-14
forum: General Help
---

### Post by Adler on 2010-10-14
Hi All,

I've been Linux / UBUNTU user for years. I find myself between a rock and hard place. None of my external HDD drives will mount. I want to ideally store everything on my 1TB drive, but nothing seems to work. 

Once I get everything on my 1TB drive, I'll make the conversion to 10.10. 10.10 does let me open my drives. Strange. But, I often goof with everything.LOL!

[[IMG]http://img233.imageshack.us/img233/5728/unabletomountdrive.th.png[/IMG]](http://img233.imageshack.us/i/unabletomountdrive.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by luvshines on 2010-10-14
Maybe stupid question but is there the /media directory ??

Did you try mounting it with command line:
```
sudo fdisk -l

## If you see your device listed there /dev/sd<something>
sudo mkdir -p /media/myhdd
sudo mount /dev/sd<something> /media/myhdd
```

---

### Post by Adler on 2010-10-14
> **luvshines said:**
> Maybe stupid question but is there the /media directory ??

Did you try mounting it with command line:
```
sudo fdisk -l

## If you see your device listed there /dev/sd<something>
sudo mkdir -p /media/myhdd
sudo mount /dev/sd<something> /media/myhdd
```

I have this, funny, that I can not do this myself..

jjmacey@jjm-laptop:~$ sudo fdisk -l
[sudo] password for jjmacey: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00039e40

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59767   480075776   83  Linux
/dev/sda2           59767       60802     8308737    5  Extended
/dev/sda5           59767       60802     8308736   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeec787db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    7  HPFS/NTFS
jjmacey@jjm-laptop:~$

---

### Post by luvshines on 2010-10-14
From that output, you can see that /dev/sdb1 is 1TB HDD

```
sudo mkdir /media/myhdd
sudo mount /dev/sdb1 /media/myhdd
```

---

### Post by luvshines on 2010-10-14
Just curious to know, did it work ?

---

### Post by Adler on 2010-10-15
luvshines,

No, it did not work.

jjmacey@jjm-laptop:~$ sudo mkdir /media/myhdd
mkdir: cannot create directory `/media/myhdd': No such file or directory
jjmacey@jjm-laptop:~$ 

This is an external 1 Tb drive,

Thanks for your help.

---

### Post by luvshines on 2010-10-15
Aah!! My mistake. If you see the mkdir command between Comment #2 and #4, I missed -p the second time I wrote

**Try mkdir with -p option.**

---

### Post by Adler on 2010-10-15
luvshines,

Let's start this again. LOL!

When I plug in any of my 2 external drives I get the error message: unable to mount file system. 

From bash / shell what is that command line? Thanks in advance for the replies. 

Regards,

JJMacey
Phoenix, Arizona

---

### Post by coffeecat on 2010-10-15
> **Adler said:**
> jjmacey@jjm-laptop:~$ sudo mkdir /media/myhdd
mkdir: cannot create directory `/media/myhdd': No such file or directory
jjmacey@jjm-laptop:~$ 

Go back to luvshines' first question. That sounds as though there is no /media directory. Before you do anything else, post the output of:

```
ls /m*
```

You say that none of your hard drives will automount. Rather than trying to manually mount them, let's troubleshoot this one.

---

### Post by luvshines on 2010-10-15
> **coffeecat said:**
> Go back to luvshines' first question. That sounds as though there is no /media directory. Before you do anything else, post the output of:

```
ls /m*
```

You say that none of your hard drives will automount. Rather than trying to manually mount them, let's troubleshoot this one.

Actually in the process, I was try to make that directory by mkdir -p, so that if absence of /media is the real problem, that will be solved automatically ;)

I though I would ask Adler to try other external disks/USB and see if they now start automounting, once I get this one by command line :D

---

### Post by coffeecat on 2010-10-15
> **luvshines said:**
> Actually in the process, I was try to make that directory by mkdir -p, so that if absence of /media is the real problem, that will be solved automatically ;)

I though I would ask Adler to try other external disks/USB and see if they now start automounting, once I get this one by command line :D

I quite agree, but it would be nice to see if /media is missing before it gets (re)instated by mkdir -p. :) That might explain his automounting problem. I have a feeling you were right on the button with that suggestion in your first post.

---

### Post by luvshines on 2010-10-15
> **coffeecat said:**
> I quite agree, but it would be nice to see if /media is missing before it gets (re)instated by mkdir -p. :)

re(instated). Is it ??
I don't think the directory is modified at all if it's already existing.
Newayz, leave it. We can fight/argue/kill-each-other over that in some other thread maybe :lolflag:
At present the concern is Adler's /media directory ;)

---

### Post by coffeecat on 2010-10-15
> **luvshines said:**
> re(instated). Is it ??

Try (re)created. :wink:

---

### Post by luvshines on 2010-10-15
> **coffeecat said:**
> Try (re)created. :wink:

Anything you say !!

PS: Are we kind of bumping the thread with OP not responding :guitar:

I hope no Mods around here to mark this CLOSED :P

---

