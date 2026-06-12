---
title: "fstab and UUIDs"
date: 2011-10-18
forum: General Help
---

### Post by Fraoch on 2011-10-18
Hello:

I just reinstalled 11.10 from scratch and I had one niggling problem regarding mounting a drive.  The problem was that the /dev/sdxx designations would move around each boot, I guess based on the order the drives started up.

Easily fixed, I specified the drives by UUID in fstab.

Except for one thing - my swap space doesn't have a UUID and must be specified by /dev/sdxx.  This is a little uncomfortable, I think it would be quite bad for the system to have its swap space suddenly inaccessible on boot.

What do I do?  If I keep it like this I'm worried this problem could come up when I change drives or if I start with removable media installed.

Output of blkid:

```
/dev/sda1: LABEL="backup" UUID="7106b2d0-f606-49b9-93cc-6aeb2cf202da" TYPE="ext4" 
/dev/sda2: LABEL="Music" UUID="13024ea4-d52a-4e12-b818-6984c23b3c96" TYPE="ext3" 
/dev/sdb1: TYPE="swap" 
/dev/sdb2: UUID="24b4457e-1579-4f60-8ca6-d2e55663c07b" TYPE="ext4" 
/dev/sdc1: UUID="09bad263-5d38-4906-9fa6-47ba4dda0c64" TYPE="ext4"
```

As you see, no UUID for the swap partition.

---

### Post by hwttdz on 2011-10-18
UUID of swap partition:

```
blkid|grep swap|head -n 1|perl -pe 's/:.*//;s/\/dev\///'|xargs -I{} bash -c "ls -l /dev/disk/by-uuid|grep {}"|awk '{print $8}'
```

i.e. get where it is right now, look at the disks attached by uuid, find which one corresponds to where it is now, that's the uuid.  Also, slight weirdness, I have 2 swaps (apparently I have a ramswap, I don't know what's going on there), so the head -n 1 grabs the first, if you have more than one swap I'll assume you can figure out how to apply this for each one.

---

### Post by Fraoch on 2011-10-18
[QUOTE=hwttdz;11362345]```
blkid|grep swap|head -n 1|perl -pe 's/:.*//;s/\/dev\///'|xargs -I{} bash -c "ls -l /dev/disk/by-uuid|grep {}"|awk '{print $8}'
```

Thanks for the response, but this command gives me no output, I'm just back at the prompt.

This either indicates my swap indeed has no UUID as there was nothing to find or that I'm doing something wrong, which could be likely.;)

---

### Post by tgm4883 on 2011-10-18
Your SWAP doesn't have a UUID, which is odd. Here is my output of blkid

```

/dev/sda1: UUID="1ae54af3-b5ed-4acc-8a7e-3e32ef31ac28" TYPE="ext4" 
/dev/sda5: UUID="3315b3ea-9531-4aca-8359-667b0669957c" TYPE="ext4" 
/dev/sdb1: UUID="3b21f682-e17c-4e82-89ee-4738f747e8e7" TYPE="ext4" 
/dev/sdb5: UUID="05e46aff-9987-43b1-83d3-14fa01e5129e" TYPE="swap" 

```

---

### Post by Fraoch on 2011-10-18
> **tgm4883 said:**
> Your SWAP doesn't have a UUID, which is odd.

It's good (and bad) to know this isn't normal, then.  In searching around I see there's a program to generate 128-bit UUIDs (uuidgen) but not 64-bit UUIDs.

Perhaps it's related to the somewhat chaotic install, I attempted to reinstall 20 or 30 times yesterday (having lots of problems) and must have made that swap partition almost as many times.  I made sure to delete the partition every time but towards the end I was getting desperate and might have skipped something.

---

### Post by hwttdz on 2011-10-18
Can you post the output of:

ls -l /dev/disk/by-uuid

---

### Post by Fraoch on 2011-10-18
> **hwttdz said:**
> Can you post the output of:

ls -l /dev/disk/by-uuid

I did this when I was first modifying fstab which is when I noticed my swap isn't listed:

```
lrwxrwxrwx 1 root root 10 2011-10-18 10:49 09bad263-5d38-4906-9fa6-47ba4dda0c64 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2011-10-18 10:49 13024ea4-d52a-4e12-b818-6984c23b3c96 -> ../../sda2
lrwxrwxrwx 1 root root 10 2011-10-18 10:49 24b4457e-1579-4f60-8ca6-d2e55663c07b -> ../../sdb2
lrwxrwxrwx 1 root root 10 2011-10-18 10:49 7106b2d0-f606-49b9-93cc-6aeb2cf202da -> ../../sda1
```

The swap is on sdb1, which is conspicuously absent.

On install, the swap was on sda1, which is logical (first partition of the first drive) but then I plugged in my backup and music drive and the designations changed.

---

### Post by matt_symes on 2011-10-18
Hi

Maybe you can create a new UUID for swap using

```
tune2fs
```Take a look at this.

```
matthew@matthew-Aspire-7540:~$ sudo blkid | grep sda2
/dev/sda2: LABEL="sda2" UUID="f4cd43e1-48e2-4540-aa52-e2a0eb1656e0" TYPE="ext4" 
matthew@matthew-Aspire-7540:~$ sudo tune2fs -U random /dev/sda2
tune2fs 1.42-WIP (9-Oct-2011)
matthew@matthew-Aspire-7540:~$ sudo blkid | grep sda2
/dev/sda2: LABEL="sda2" UUID="722ff581-900b-49e3-be28-78ce7b123710" TYPE="ext4" 
matthew@matthew-Aspire-7540:~$
```It's not a swap partition above but it should work for you.

EDIT: You may need a reboot if the problem is no UUID after adding one using the above method.

Kind regards

---

### Post by CatKiller on 2011-10-18
You could just make a new swap partition. Gparted will do it easily enough. Shouldn't take very long.

---

### Post by Elfy on 2011-10-18
Sometime ago - [http://ubuntuforums.org/showthread.php?t=880108](http://ubuntuforums.org/showthread.php?t=880108)

specifically post 7

---

### Post by Fraoch on 2011-10-18
> **matt_symes said:**
> Hi

Maybe you can create a new UUID for swap using

```
tune2fs
```Take a look at this.

```
matthew@matthew-Aspire-7540:~$ sudo blkid | grep sda2
/dev/sda2: LABEL="sda2" UUID="f4cd43e1-48e2-4540-aa52-e2a0eb1656e0" TYPE="ext4" 
matthew@matthew-Aspire-7540:~$ sudo tune2fs -U random /dev/sda2
tune2fs 1.42-WIP (9-Oct-2011)
matthew@matthew-Aspire-7540:~$ sudo blkid | grep sda2
/dev/sda2: LABEL="sda2" UUID="722ff581-900b-49e3-be28-78ce7b123710" TYPE="ext4" 
matthew@matthew-Aspire-7540:~$
```It's not a swap partition above but it should work for you.

EDIT: You may need a reboot if the problem is no UUID after adding one.

Kind regards

Ah, I think it won't do this because a swap filesystem isn't a filesystem tune2fs can work with:

```
$ sudo tune2fs -U random /dev/sdb1
tune2fs 1.41.14 (22-Dec-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.
```

Thanks for all the help guys, I appreciate it!

---

### Post by Fraoch on 2011-10-18
> **forestpiskie said:**
> Sometime ago - [http://ubuntuforums.org/showthread.php?t=880108](http://ubuntuforums.org/showthread.php?t=880108)

specifically post 7

Ah yes post 10 got it!

[http://ubuntuforums.org/showpost.php?p=5542571&postcount=10](http://ubuntuforums.org/showpost.php?p=5542571&postcount=10)

I have a UUID for my swap now, I haven't entered it into fstab yet but there's no reason it shouldn't work now.

Thanks for your help everyone!  I'll mark the thread as solved after I enter it into fstab, reboot and everything is working.

---

### Post by matt_symes on 2011-10-18
Hi

> **Fraoch said:**
> Ah, I think it won't do this because a swap filesystem isn't a filesystem tune2fs can work with:

```
$ sudo tune2fs -U random /dev/sdb1
tune2fs 1.41.14 (22-Dec-2010)
tune2fs: Bad magic number in super-block while trying to open /dev/sdb1
Couldn't find valid filesystem superblock.
```Thanks for all the help guys, I appreciate it!

Well i did not know that. However, thinking about it, it does make sense. :D

I'm glad it's fixed. make2fs is the way to go. I wonder why it failed on your system though ?

Kind regards

---

### Post by Elfy on 2011-10-18
> **matt_symes said:**
> Hi



Well i did not know that. However, thinking about it, it does make sense. :D

I'm glad it's fixed. make2fs is the way to go. I wonder why it failed on your system though ?

Kind regards

I didn't either till I said use tune2fs in that thread - such is life and learning :)

---

### Post by Fraoch on 2011-10-18
> **matt_symes said:**
> Hi



Well i did not know that. However, thinking about it, it does make sense. :D

I'm glad it's fixed. make2fs is the way to go. I wonder why it failed on your system though ?

Kind regards

Yeah, kinda bizarre.  It could be related to the fact that I created and deleted that partition dozens of times, I might have missed it once and used an existing partition from a previous install attempt.  (I had a helluva day yesterday trying to reinstall Oneric!)

Thanks again.

---

### Post by matt_symes on 2011-10-18
Hi

> **forestpiskie said:**
> I didn't either till I said use tune2fs in that thread - such is life and learning :)

....and i even meant mkswap and not make2fs in my previous post. I can be _so_ dumb sometimes :D

Think i might just watch TV tonight :-k

Kind regards

---

