---
title: "Disk check complaining about a drive that doesn't exist"
date: 2012-05-05
forum: General Help
---

### Post by x-shaney-x on 2012-05-05
Since I installed 12.04, it had done 3 or 4 boot-up disk checks.
Each time it has complained about a particular UUID being missing or not ready and asks if I want to wait, skip or manually recover.

The thing is, all partitions are accounted for and that UUID does not exist.

Also, this was a completely fresh install with no old config files copied over or anything so I'm not sure what this UUID is it is seeing?

---

### Post by hal8000 on 2012-05-05
Post the output of:

sudo blkid


and also


sudo cat /etc/fstab


If the UUID has been logged in /var/log/messages

you may also be able to post the UUID that Ubuntu is complaining about.

---

### Post by x-shaney-x on 2012-05-05
$ sudo blkid
```
/dev/sda1: LABEL="PQSERVICE" UUID="2058BA2458B9F91C" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="18DEBA91DEBA66A2" TYPE="ntfs" 
/dev/sda3: LABEL="WINDOWS" UUID="F0E4BBCEE4BB94F6" TYPE="ntfs" 
/dev/sda5: LABEL="DATA" UUID="46BB-CF88" TYPE="vfat" 
/dev/sda6: UUID="847fdfd3-d3fa-418c-abbf-c8fb5bd20b37" TYPE="swap" 
/dev/sda7: LABEL="LINUX1" UUID="145fe43a-f7d2-4a16-a4ec-2b1c3adb0ddd" TYPE="ext4" 
/dev/sda8: LABEL="LINUX2" UUID="104ebc57-e404-4e72-bb2e-216d86ea81c9" TYPE="ext4" 
/dev/sda9: LABEL="LINUX3" UUID="8877c7d7-3cb6-4c57-bead-11466c8a3baa" TYPE="ext4" 
/dev/sda10: LABEL="LINUX4" UUID="b5c01654-869b-409f-8809-04abdef44615" TYPE="ext4"
```

$ sudo cat /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=145fe43a-f7d2-4a16-a4ec-2b1c3adb0ddd /               ext4    errors=remount-ro,user_xattr 0       1
# /mnt/Data was on /dev/sda5 during installation
UUID=46BB-CF88  /mnt/Data       vfat    utf8,umask=007,gid=46 0       1
# swap was on /dev/sda6 during installation
UUID=382ee088-4907-4220-b666-6607b7f113ee none            swap    sw              0       0
```

Strangely enough, I have no /var/log/messages file at all and I have been unable to find anything in any logs showing the boot message.

I can't remember the actual UUID other than it was a long, multi-part ext style ID that starts with 836

---

### Post by hal8000 on 2012-05-05
Next time it happens write down the exact UUID.

Only thing I notice is you have 4 linux partitions, but no separate /home partition. Should your / partition become corrupted then home is also on the same partition.

In the future I would recommend /home on a separate partition.
Having said that, I have never ever lost a single byte of data from any linux partition. They are far more secure and  robust than any windows filesystem.

---

### Post by Cheesemill on 2012-05-05
Your fstab file has an incorrect entry for your swap partition.
Compare your fstab with the output of blkid and you'll see what I mean.

This can happen if you have more than one Linux installation using the same swap file.
When you install certain distros they insist on re-formatting the swap partition (even if there is no need), hence changing its UUID.

I would boot into all of your different installations and check the fstab file in them, just to make sure they are all actually using the swap partition.

---

### Post by x-shaney-x on 2012-05-05
@ hal8000

I don't have a separate home but all my important stuff  (media, pictures etc) are on the Data partition and linked to my home

@ Cheesemill

I didn't notice that but I think you have solved the problem.
My guess is the next time I see that message I will find I was mistaken with those numbers and the swap partition is the problem one.
I have looked at gnome system monitor and it does show swap as unavailable.
I did actually install kubuntu after ubuntu so that would explain it.

I will blame my new glasses :)

---

### Post by dcstar on 2012-05-05
> **x-shaney-x said:**
> 
I didn't notice that but **I think you have solved the problem**.


Then** Mark** the thread.

---

### Post by x-shaney-x on 2012-05-06
Now marked.  Just wanted to make sure it was indeed solved.

---

