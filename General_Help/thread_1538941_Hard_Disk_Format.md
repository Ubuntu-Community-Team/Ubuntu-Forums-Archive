---
title: "Hard Disk Format"
date: 2010-07-25
forum: General Help
---

### Post by sandyd on 2010-07-25
Im starting to get some bad blocks on my HD, and their right on my gentoo partition. I can fix this with a format.

What im thinking of is this (and can someone help me figure out the commands for it?)

I have a ubuntu partiiton on the disk that I don't really use. Its much much larger than the gentoo partition
I, however have a ton of movies and stuff that I still need.
Is it possible to delete everything except the movies, and stuff I need (they will be stored in /opt) and dd the gentoo parition right onto the ubuntu partition, while ignoring I/O errors? The errors are just caused by some files that I have backed up, and I don't care if I lose them.

Secondly, would it be possible to DD/CP it to a folder onto the ubuntu disk, while preserving permissions? If I can, I can simply dd/cp it into a folder, and wipe the gentoo partition and toss everything back on. (it would be a good time to upgrade to ext4)

---

### Post by lmarmisa on 2010-07-25
Do you know the **tar** command? **tar** is a classic command from the Unix old times.

[https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)

I consider that **tar** is a more appropriate command than **dd**. **tar** is able to preserve the permissions of the files.

Another options would be to use **cp -av** or even Clonezilla [http://www.clonezilla.org](http://www.clonezilla.org)

---

### Post by nmaster on 2010-07-26
is /opt mounted on a separate partition? if not, you should do that, it'll make this a lot easier.  i'd suggest [http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page) for archiving the gentoo and then restoring to what is now an ubuntu parition.

---

### Post by sandyd on 2010-07-26
yup, but the problem is that I got some corrupt stuff there, which I need tar to ignore. I havent found out how to do that... yet. I just need tar to ignore any I/O errors its getting and continue on.

---

### Post by dino99 on 2010-07-26
try to repair this partition:

to check and know the problems:

fsck -n /dev/sdxx (change xx by your real partition)

to repair it:

fsck -y /dev/sdxx

**** might be made from any other partition, for security ****

---

### Post by sandyd on 2010-07-26
> **dino99 said:**
> try to repair this partition:

to check and know the problems:

fsck -n /dev/sdxx (change xx by your real partition)

to repair it:

fsck -y /dev/sdxx

**** might be made from any other partition, for security ****

already done. shows disks got bad blocks, which is the reason why im trying to move the stuff in the gentoo partition while ignoring the I/O errors.

---

