---
title: "Stumped - won't boot"
date: 2011-02-07
forum: General Help
---

### Post by cjhabs on 2011-02-07
Hi
Running 10.04 as the only OS on a HP desktop - been running fine for months.
Did an update - probably hadn't done one for a couple of months - may be a red herring.
The system appeared to crash while inactive.
Trying to boot - I get the Ubuntu 10.04 screen for a short while then it goes to blank screen with a flashing cursor at the top - occasionally it will give me an error that /home is not ready - skip or manual fix.

I have sda1 = ext4 root
sda2 = swap
sda3 = ext4 home
sdb1 = ntfs

I removed sdb1 from fstab as initially it was complaining about this drive not being ready.
The error switched to complaining about /home.
I am able to mount both of those filesystems with no problem manually.
I ran mke3fs on /home (I forgot the -n parameter! but no problem as I have good backups) - same error - complains about /home not being available at boot even though I can always manually mount it from live cd or manual recovery.

I can rebuild this system - and I may as it was upgraded from 9.10 - I may do a fresh 10.04, but I would like to fix the boot problem in case something like this happens again when I actually care about fixing it.

I recreated the grub2 configs - I don't have the command to hand, something like:
sudo update-grub --root-directory=/mnt/boot/grub /dev/sda

Anyway, any insight would be greatly appreciated.

Thanks

Chris

---

### Post by marin123 on 2011-02-07
do you have proprietary drivers for your graphic card? if you do, maybe xorg update did that.
check this out, maybe it helps. [http://ubuntuforums.org/showthread.php?t=1663916](http://ubuntuforums.org/showthread.php?t=1663916)

and make sure you reinstall drivers the same way you installed them, example: if you downloaded drivers from ati website like i did, you need to download the same file again and run it.

---

### Post by cjhabs on 2011-02-07
Thanks - the single user boot info is very useful. However, I had a complete brain fart and omitted what is probably the most important bit of information!

Although I can manually mount the /home filesystem with no problem - when I run e2fsck against it, it complains about the super blocks - I can't remember the exact message, I'll need to post it when I get home in the evening. This happened before and after running mke2fs.
I tried it with alternate superblock numbers but no go.
When I mount the file system it looks fine - all the files are there.

Thanks - and sorry for the omission.

---

### Post by marin123 on 2011-02-07
> **cjhabs said:**
> Thanks - the single user boot info is very useful. However, I had a complete brain fart and omitted what is probably the most important bit of information!

Although I can manually mount the /home filesystem with no problem - when I run e2fsck against it, it complains about the super blocks - I can't remember the exact message, I'll need to post it when I get home in the evening. This happened before and after running mke2fs.
I tried it with alternate superblock numbers but no go.
When I mount the file system it looks fine - all the files are there.

Thanks - and sorry for the omission.

i cant help you on this one... :(

if i were in your place, i would backup /home and do a fresh install...

i hope theres someone here that can help you...

---

### Post by cjhabs on 2011-02-07
Thanks - I have no problem rebuilding, I would just like to figure out how to fix it in case it happens when rebuilding would be a p.i.t.a

Thanks for your help, I'll keep digging.

---

### Post by cjhabs on 2011-02-08
Well - no takers on the e2fsck issue, so I did try a little more:
I realized that I had made a pig's ear of running mke2fs, so I reran it with -U uuid (as I was too lazy to edit fstab) and -t ext4.
e2fsck ran fine. 
It mounted manually with no problem.
On boot, it complained about /home not being ready - yet as soon as I entered "manual recovery" mode and mounted /home it was fine.
So I rebuilt the system - my data drive was untouched and OK so the rebuild took me 2 hours including all customizations from scratch (previously I had upgraded from 9.10).

So the problem is still a mystery but the system is up and running. I will mark it as solved anyway.

---

