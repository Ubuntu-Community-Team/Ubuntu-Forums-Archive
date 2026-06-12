---
title: "I have to skip the automatic fsck because it hangs"
date: 2010-11-30
forum: General Help
---

### Post by burton247 on 2010-11-30
Basically the title says it all. The fsck that runs every certain amount of mounts hasn't worked think upgrading to 10.10 I believe. I have to skip the checks to get my system to boot, this is starting to get annoying and I want try and fix it.

Has anyone got any ideas?

---

### Post by matt_symes on 2010-11-30
Hi

You can disable the file system check by editing your /etc/fstab file. There are a number of columns for each entry. The last entry is the file system check option. A value of zero will ensure no file system check.

The /etc/fstab file format is explained here

[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

If you want post your /etc/fstab file here and we can take a look.

It would be worth trying to find out why fsck is hanging in the first place. It is a useful utility.

Boot into a LiveCD and run it after ensuring the file system is not mounted. This will check the partition.

Kind regards

---

### Post by deserthowler on 2010-11-30
How long does it hang?  It might be resolving an issue for you.

Earl

---

### Post by burton247 on 2010-11-30
It never starts the check, it says it is going to but it doesn't. I could disable but I'd much rather get it working, as you said, it is rather useful. I've got an arch partition on here so I can run fsck on it from there. Maybe running it will cause it to fix itself?

---

