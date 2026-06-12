---
title: "problem mounting"
date: 2009-11-03
forum: General Help
---

### Post by RandomQuestion on 2009-11-03
I recently upgraded to 9.10 from 9.4, only the upgrade was unsuccessful and I have yet to be able to boot into ubuntu. This is a disappointing problem on it's own, but it's not the reason for the post. I just figure some quick background might be helpful.

relevant system architecture info:
3 Drives: 1 windows, 1 linux, 1 ntfs partition for shared data

Since I can't boot into my ubuntu drive, I figured I would boot into the live disk so that I can mount and copy out my home folder and/or any files I might want. Here in lies the problem.

A check of fdisk -l shows my linux partition (in this case sdb1) along with my other partitions. A look in the /dev folder shows sdb but not the partition sdb1.

when I try to mount "mount -t ext4 /dev/sdb1 /mnt/oldlin" I get the following error: "mount: special device /dev/sdb1 does not exist"

yes, the fs is ext4 and yes I created /mnt/oldlin.

I don't really know what I'm missing here. 

I welcome suggestions if there is another way to go about this. Like I stated earlier, I just want to back up my home folder and check for anything else I might want. 

Most of it is already backed up so I'm not too worried, but I'd like to make sure that I have it all.

---

### Post by IllegalCharacter on 2009-11-04
Do you have separate hard drives, or are those just different partitions?
Is there a /dev/sda1?

---

### Post by RandomQuestion on 2009-11-04
yep separate hard drives:
/dev/sda
/dev/sdb
/dev/sdc

/dev/sda1 = windows partition

/dev/sdb1 = linux
/dev/sdb2 = extended
/dev/sdb3 = linux swap

/dev/sdc1 = ntfs partition for shared data

good question though because in fact there is no sda1 or sdb1 in the /dev folder. However, sdc1 is there and I mounted it and everything with that is working fine.

---

### Post by IllegalCharacter on 2009-11-04
What does

```
ls /dev/sd*
```

give you?

---

### Post by RandomQuestion on 2009-11-04
/dev/sda  /dev/sdb  /dev/sdc  /dev/sdc1

---

### Post by IllegalCharacter on 2009-11-04
Hmm, it appears to not be seeing your partitions.

I've heard that sometimes Karmic has trouble mounting drives, try using a 9.04 LiveCD and see if that changes anything.

---

### Post by RandomQuestion on 2009-11-04
well, at least I don't feel like it's me just being retarded. 

I find it strange that I can fdisk -l and it shows them but they aren't being seen...

I'll give your suggestion of 9.04 LiveCD a try. thanks.

---

### Post by RandomQuestion on 2009-11-04
The 9.04 LiveCD did the trick without a hitch. 

I don't understand what's going on with 9.10 :-/

---

