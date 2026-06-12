---
title: "init:  mountall main process (471) terminated with status 3"
date: 2010-02-26
forum: General Help
---

### Post by ucal on 2010-02-26
Hi all, just installed arch linux on a different partition, and now I can't boot into ubuntu.  Title is the error code, let me know what additional information you need, and I'll do my best to supply it.

---

### Post by ucal on 2010-02-28
bump.

The number in parentheses is changing if that helps.  It's seemingly random.

---

### Post by MJBoa on 2010-02-28
Hmm, when does this show up? And what happens after this? That number is the process id, by the way.

If you can boot into arch and mount your ubuntu partition, post the contents of the /etc/fstab file on that partition. Also, the output of 
```
sudo blkid
```

---

### Post by ucal on 2010-03-01
Well, lately it's been trying to do a file system check, and if I let it run through that, it shows up after that.  Then it boots into a recovery shell.  

blkid.

```
/dev/sda1: LABEL="PQSERVICE" UUID="AC304642304613AC" TYPE="ntfs"
/dev/sda2: UUID="2496d470-0b65-4bd9-8ac9-28205438fce2" TYPE="ext3"
/dev/sda4: UUID="0C5C528D5C527206" TYPE="ntfs"
/dev/sda5: UUID="e8fa8407-f0b5-4bd5-b531-0b487bba2456" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda6: UUID="964a84aa-d988-4ba5-9801-3fe90f10fbd3" TYPE="swap"
```

fstab

```
#
# /etc/fstab: static file system information
#
# <file system>        <dir>         <type>    <options>          <dump> <pass>
none                   /dev/pts      devpts    defaults            0      0
none                   /dev/shm      tmpfs     defaults            0      0

#/dev/cdrom             /media/cd   auto    ro,user,noauto,unhide   0      0
#/dev/dvd               /media/dvd  auto    ro,user,noauto,unhide   0      0
#/dev/fd0               /media/fl   auto    user,noauto             0      0

/dev/sda2 / ext3 defaults 0 1
/dev/sda6 swap swap defaults 0 0

```

---

### Post by ucal on 2010-03-05
bump.

---

### Post by ucal on 2010-03-07
bump.

---

### Post by aulli on 2010-03-19
Hi!

I had the same problem, and my hdd produced clicking noises.
I ran "fsck" (filesystem check) in the recovery shell, had to enter "y" (yes) a few times and this solved the problem.

---

### Post by yichuan on 2010-04-09
> **aulli said:**
> Hi!

I had the same problem, and my hdd produced clicking noises.
I ran "fsck" (filesystem check) in the recovery shell, had to enter "y" (yes) a few times and this solved the problem.


Love you man...you saved my entire week...

---

### Post by Guilden_NL on 2010-04-11
Phew, quick check to this post and I saved an hour at least.  Thanks for the spot on advice aulli!

---

