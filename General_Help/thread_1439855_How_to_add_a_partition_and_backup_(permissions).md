---
title: "How to add a partition and backup (permissions)"
date: 2010-03-26
forum: General Help
---

### Post by bswanboat on 2010-03-26
I have formated a partition on the second hard drive to use for backups. I have been able to create a directory using sudo but I have not succeeded in changing permissions so Bill can use it for backups.

sudo chmod a+rw BackUp runs without errors but doesn't change permissions.
sudo  chmod +666 Backup just brings up the see man message.

How can the permission be changed?

---

### Post by darolu on 2010-03-26
This should work:
```
$ sudo chmod **-R** a+rw /path/to/your/mountpoint/directory

or

$ sudo chmod **-R** 666 /path/to/your/mountpoint/directory
```

The -R (--recursive can be used also) change files and directories recursively.

You can also edit your fstab file so permissions are added when the drive is mounted automatically.

Read this thread to understand how fstab file works: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by bswanboat on 2010-03-26
Thanks for the response! It is helpful. I alse tried the root terminal and finally got something to work.

---

