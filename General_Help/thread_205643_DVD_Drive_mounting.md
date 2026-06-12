---
title: "DVD Drive mounting"
date: 2006-06-28
forum: General Help
---

### Post by _simon_ on 2006-06-28
Both machines in our house are doing the same thing.

Both have dapper installed (not upgrades)

What's happening is that sometimes the CD or DVD is recognised no problem but other times it will either show the CD / DVD as empty or show 2 or more files with question marks for names.

I noticed that if I used the MOUNT option in Cedega (unmount then remount) that Dapper can then read the CD or DVD properly.

Why is this happening?
How can I prevent it?

My fstab looks like this:

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /home           ext3    defaults        0       2
/dev/hdb2       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by _simon_ on 2006-06-29
Does no-one else get this?

Must be other people as it's happening on the 2 machines here, both with different drives.

---

