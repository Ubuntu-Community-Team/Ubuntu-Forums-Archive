---
title: "rsync not maintianing owners"
date: 2012-06-25
forum: General Help
---

### Post by AlexBooton on 2012-06-25
Hi,

I'm trying to use rsync to make a backup to an external usb drive.

But it isn't preserving users and groups.

Here's the command I'm using.  

Only the options are relevant here but I'm showing it all jic.

I do have the -o option to preserve ownership and I'm running as root which I think is necessary to preserve ownership.  

In fact I just noticed I have -o twice.  

It didn't work on my first try so I added -o without noticing I already had -tgo.:

```
rsync -h --progress --stats -r -tgo -o -p -l -D --update --exclude=**/*tmp*/ --exclude=/media/12.04bu/luckybu/*/** --exclude=**/*cache*/ --exclude=/mnt/*/** --exclude=/media/*/** --exclude=**/lost+found*/ --exclude=**/*trash*/ --exclude=/cdrom/ --exclude=/proc/ --exclude=/mnt/ --exclude=/sys/ --exclude=/media/ --exclude=/dev/ / /media/12.04bu/luckybu/
```

Am I missing something?  Why doesn't this preserve owners?

Thanks,

AB

---

### Post by ajgreeny on 2012-06-25
How is the external drive formatted?

It really needs to be a Linux filesystem eg ext2/3/4 for all permissions to be retained.  If you want to retain permissions you can still do it to a fat32 system but will have to archive the backedup files and then just have the archive on the fat32 drive, not separate files/folders.

There is no need to run it as root just to keep permissions.

---

### Post by papibe on 2012-06-25
Hi AlexBooton.

What kind of filesystem has the external usb drive?

Regards.

---

### Post by AlexBooton on 2012-06-25
Aha!  I should have realized it had to be on a Linux file system.

Thanks,

AB

---

