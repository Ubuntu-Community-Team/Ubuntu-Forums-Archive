---
title: "Bad Inode Count"
date: 2010-09-15
forum: General Help
---

### Post by uRock on 2010-09-15
Hello.

My system locked up, so I completed a hard shutdown and now I am stuck with the init not found screen with CLI(initramfs), but I have no clue what to do.

The other OSes in grub still boot.

Is there a way to fix it or do I need to reinstall.

Thanx,
uRock

---

### Post by JK3mp on 2010-09-15
Hmmmmm... I'll google and let ya know if i find anything. Havn't made any hardware or systemconfig changes have you?

---

### Post by uRock on 2010-09-15
> **JK3mp said:**
> Hmmmmm... I'll google and let ya know if i find anything. Havn't made any hardware or systemconfig changes have you?
Nope. I have done some googling, but haven't found anything useful, yet.

---

### Post by uRock on 2010-09-15
From what I have seen the / partition has issues, so I ubuntu am reinstalling.

Thanks JK3mp.

uRock

---

### Post by uRock on 2010-09-15
I haven't started reinstalling yet as my CD/DVD-ROM has decided it doesn't wanna read a disk that I know is good and I don't have time to use the USB to install right now. Got lots of homework due today.

If anyone has any ideas for using initramfs to get things working again, then please share your thoughts.

Thanks,
uRock

---

### Post by blueridgedog on 2010-09-15
I suggest you boot on a LiveCD and run fsck on the partition while it is unmounted.

---

### Post by ajgreeny on 2010-09-15
> **blueridgedog said:**
> I suggest you boot on a LiveCD and run fsck on the partition while it is unmounted.
+1
Just what I was going to say, but I then realised you will need to get your CD/DVD drive to work first.

Once you do that, simply boot to live CD and use command ```
sudo e2fsck /dev/sdx#
```sdx# being the faulty ubuntu partition.

---

### Post by uRock on 2010-09-15
Getting ready to restart to see how it works. fsck did a few changes, so I am hopeful of not having to reinstall. Here is what it did;

```
ubuntu@ubuntu:~$ sudo e2fsck /dev/sda2
e2fsck 1.41.11 (14-Mar-2010)
/dev/sda2 contains a file system with errors, check forced.
Pass 1: Checking inodes, blocks, and sizes
Deleted inode 800546 has zero dtime.  Fix<y>? yes

Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences:  -632894
Fix<y>? yes

Free blocks count wrong for group #19 (26486, counted=26487).
Fix<y>? yes

Free blocks count wrong (2839846, counted=2839847).
Fix<y>? yes

Inode bitmap differences:  -800546
Fix<y>? yes

Free inodes count wrong for group #97 (4, counted=5).
Fix<y>? yes

Free inodes count wrong (786396, counted=786397).
Fix<y>? yes


/dev/sda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda2: 178371/964768 files (0.1% non-contiguous), 1017761/3857608 blocks
```

---

### Post by uRock on 2010-09-15
Well, that totally got me back up and running. Thanks for the help fellas!:D

uRock

---

### Post by ajgreeny on 2010-09-15
You're very welcome.  It is quite unusual for a forced hard shutdown to cause problems these days, but when it does, fsck seems to sort it fairly easily.

---

### Post by JK3mp on 2010-09-15
> **uRock said:**
> Well, that totally got me back up and running. Thanks for the help fellas!:D

uRock

Sweet! Congrats...

---

### Post by uRock on 2010-09-15
> **JK3mp said:**
> Sweet! Congrats...
Thanks!:D

---

### Post by uRock on 2010-09-24
Have had to run this again, already. Starting to wonder what is causing the lockups and in turn causing me to have to run this.

---

### Post by uRock on 2010-09-25
Have to run this yet again.

Does anyone know what program could possibly be locking up ubuntu and messing up the inode count at the same time?

---

