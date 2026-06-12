---
title: "HDD Busy - fsck.ext3"
date: 2009-11-23
forum: General Help
---

### Post by zzzBrett on 2009-11-23
I'm trying to mount a hard drive:

sudo mount /dev/sdb1 /media/HDD1

result:
mount: /dev/sdb1 already mounted or /media/HDD1 busy

In webmin I can see the following process is running that are preventing me from mounting it.

	root 	13:12 	fsck -a -C11 -t ext3 /dev/sdb1
         517 	root 	13:12 	fsck.ext3 -a -C11 /dev/sdb1

What is this fsck process, and why is it running on startup?  It is preventing my fstab from mounting the hard drives at startup.

Thanks

---

### Post by falconindy on 2009-11-23
fsck is the filesystem checker. It runs as specified on bootup by /etc/fstab. If you specify the very last option to be "0" in your fstab, checking won't take place every bootup.

---

### Post by efflandt on 2009-11-23
Normally when you boot, Linux automatically checks if it has been too long since each partition has been checked for errors, and if so, runs fsck -a on them to check and fix errors before mounting them.  Your /etc/fstab settings determine if they are checked on the first pass before mounting /, or after that for less essential partitions.  That can take awhile for a large partition.

If you post the text of your /etc/fstab someone could check if that is configured properly.  If it is all correct, maybe it is just a matter of having patience after rebooting.

To make fixed format text (like fstab) easier to read and follow tabs or columns, you can surround it with smart code tags.  Those are **code** surrounded with square brackets [ ] before the beginning of that text, and **/code** surrounded by square brackets at the end of that text.  I cannot actually type the complete tags here or they would be interpreted as code tags.

---

### Post by zzzBrett on 2009-11-24
Thanks for the responses.

---

### Post by dcstar on 2009-11-24
> **efflandt said:**
> 
.........
To make fixed format text (like fstab) easier to read and follow tabs or columns, you can surround it with smart code tags.  Those are **code** surrounded with square brackets [ ] before the beginning of that text, and **/code** surrounded by square brackets at the end of that text.  I cannot actually type the complete tags here or they would be interpreted as code tags.

Why not just say: "Use the Code feature "#" in the forum compose screen"?

---

