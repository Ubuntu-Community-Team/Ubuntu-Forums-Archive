---
title: "Boot failure, Read-Only File System"
date: 2011-01-15
forum: General Help
---

### Post by Theotherguy1 on 2011-01-15
When attempting to boot into Ubuntu 9.10 after installing 32-bit compatibility libraries, I get a crash out of the boot process with several errors complaining of a "read-only file system," leaving me in a terminal.

Running "mount -n -o remount,rw /" from the terminal and logging in allows me to access the file system as normal. Running "startx" from here starts the GUI, but mouse and keyboard input seem to be disabled.

The contents of my fstab are:
```
proc    /proc    proc    defaults    0    0

# / was on /dev/sda5 during installation
UUID=0caf7969-f5e5-4c5b-a55f-89d91a64ee04 /    ext4 errors=remount-ro 0    1

# swap was on /dev/sda6 during installation
UUID=ec25cd74-880e-434a-ab3f-9e82f1d58058 none    swap    sw
/dev/scd0    /media/cdrom0    udf,iso9660 user,noauto,exec,utf8 0    0
```Running fckdsk yields no errors in the file system.


Any ideas on what might be causing this, and how I might boot into Ubuntu again?

Thanks.

---

### Post by Theotherguy1 on 2011-01-16
Wow, I suppose I shouldn't have posted this in general help. 24 hours go by and I'm already on page 30! I'm sorry, but I must bump this. If I can't find a solution in the next couple of days, I will simply get my data off of the machine with a recovery disk and re-install ubuntu.

---

### Post by Sporktacular on 2011-01-16
Does changing errors=remount-ro to just rw allow you to boot? Or you may be able to boot normally by changing the last number of the line to 0 if you wish the keep the remount functionality. Neither really fixes the problem so much as ignores it though :(

---

