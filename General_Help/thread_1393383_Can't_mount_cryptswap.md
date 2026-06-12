---
title: "Can't mount cryptswap"
date: 2010-01-29
forum: General Help
---

### Post by amanda on 2010-01-29
I will confess that I don't fully recall what I did when I set this all up, but I was given an option to encrypt my home directory, and I took it. 

Lately, I've started seeing an occasional error on boot: my machine complains that it can't boot /dev/mapper/cryptswap1.

For a while it would just hang, but after a recent update I noticed it offering me the option to hit esc and drop into a shell to resolve the problem. Actually hitting esc, though, just lets me proceed to the login screen. 

The whole thing is (not surprisingly) kind of nervewracking because I don't know what the problem is. 

I'm on Karmic. 

Here's my fstab:

> [0 amanda@luna ~]$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a937a8a8-6320-4f3e-9636-b2a92403065f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
#UUID=73bc0726-ed56-43ca-9827-06ad56f4d98e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/cryptswap1 none swap sw 0 0


---

### Post by amanda on 2010-01-29
One source of frustration in all this is that I can't find anything in my error logs that might be a record of the problem.

---

### Post by Matej_bb on 2010-02-04
Amanda, I have the same problem (xubuntu 9.10) and from what the screen showed me and my intuition told me, I figured out that Xubuntu is trying to mount the encrypted partition BEFORE it is created. (question to me, remains why :confused: )
While your xubuntu is running (with no swap I suspect), open terminal and type
```

sudo swapon /dev/mapper/cryptswap1

```This mounted SWAP for me. (I saw it by those practical "System Load Monitor" bars I have enabled up on the panel ;) )

Now I still have to reboot and see if Xubuntu remembers what I just told it I want.

---

### Post by Anhedonia on 2010-02-24
sudo swapon /dev/mapper/cryptswap1

This delayed the crash when i tried to vim fstab by three cursor movements instead of 1.

---

### Post by Anhedonia on 2010-02-27
I added 

swapoff -a

swapon -a

to the rc.local and i dont have the problem anymore.

I cant remember who's post helped but thanks anyway.

Russ.

---

### Post by ZEROtech on 2013-03-25
In my case i moved the swap partition to a new location and i had to make it crypted again and all my data changed.
From cryptswap1 to cryptedswap so check your /dev/mapper if the cryptswap exists.
Also here is a good how to make it crypted again [http://emidio.planamente.ch/docs/linux/dm-crypt/dm-crypt-3.html](http://emidio.planamente.ch/docs/linux/dm-crypt/dm-crypt-3.html)

hope it helps

---

### Post by wildmanne39 on 2013-03-25
Thanks for sharing, please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

