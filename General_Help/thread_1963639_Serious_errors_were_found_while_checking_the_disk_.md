---
title: "Serious errors were found while checking the disk media/Windows7_OS"
date: 2012-04-22
forum: General Help
---

### Post by GameX2 on 2012-04-22
Hi,


My Windows 7 partition is automatically mounted, since my files are present on that partition, my music, documents..

This work well, the only problem I have, everytime I boot Ubuntu (11.10 64-Bits), I get that annoying message "Serious errors were found while checking the disk /media/Windows7_OS".
I have the choice to ignore (I always do that), skip mount and manual recovery.


Odd, Windows 7 work perfectly!

Here's my /etc/fstab file:


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=c610f421-8894-42f5-86ea-ed46b8c8fda3	/	ext2	errors=remount-ro	0	1
#Entry for /dev/sda2 :
UUID=B6E88D0CE88CCC55	/media/Windows7_OS	ntfs	defaults	0	2
#Entry for /dev/sda6 :
UUID=69463f2a-2ffe-4fb9-b68a-37aafd834bc9	/home	ext2	defaults,user_xattr	0	0
#Entry for /dev/sda7 :
UUID=a66160eb-8a0a-45f7-9e1b-fd3f594144e3	none	swap	sw	0	0
```


Any thought about how to stop this message from showing up?

Thanks!

---

### Post by Mark Phelps on 2012-04-23
Mounting the Win7 OS partition read-write by default is asking for trouble.  You're very fortunate that nothing has happened so far.

What you can try, is next time you're in Win7, use the option to scan the drives for errors.  It should find nothing -- but that scan should also reset the filesystem so that, when it gets mounted in Ubuntu, you no longer get error messages.

---

### Post by GameX2 on 2012-04-23
Got it solved, sorry about that.
Edited the fstab file, and changed:

```
#Entry for /dev/sda2 :
UUID=B6E88D0CE88CCC55	/media/Windows7_OS	ntfs	defaults	0	2
```

To this:

```
#Entry for /dev/sda2 :
UUID=B6E88D0CE88CCC55	/media/Windows7_OS	ntfs	defaults	0	0
```

Actually, at first, I have no idea why, my Windows partition was in read-only (First time that happened).  So I added the ''2'' myself, to FSTAB.

When I changed back the 2 to 0, the message vanished, and oddly, the partition is not in read-only anymore.


Thanks for the reply. :)

---

