---
title: "DejaDup Failure:  Questions and Issues"
date: 2012-04-22
forum: General Help
---

### Post by buzzingrobot on 2012-04-22
DejaDup failed on first use here on a 12.04 machine.  That raises some questions and comments:

1. DejaDup defaults to backing up /home to Ubuntu One.  That seems problematic because many /home directories are going to be larger than the default freebie allocation on Ubuntu One.

2. I configured DejaDup to back up /home to a partition on another drive.  That failed, with DejaDup complaining about "Permission denied" as soon as it tried to move a file to the backup drive.  That's to be expected because that drive is owned by root.  Does this mean I need to run DejaDup as root?  If I do, will it automatically run as root on future scheduled backups?

3. I want to backup, i.e., clone, the boot drive to a partition on another drive. I want to be able to restore the boot drive in bootable condition from that backup partition.  DejaDup won't let me set /dev/sda as the source drive.  Should I assume it is intended only for file backups?

---

### Post by r-senior on 2012-04-22
1. I'd agree.

2. Make a folder on the other drive and chown it to yourself and your default group. For example, if you have the other drive mounted on /mnt/backup:

```
$ sudo mkdir /mnt/backup/buzzingrobot
$ sudo chown buzzingrobot.buzzingrobot /mnt/backup/buzzingrobot
```

Then set /mnt/backup/buzzingrobot as the target for your backups. I do this and it works well.

Your username might not be buzzingrobot, but you get the idea. ;)

3. For the type of use you suggest, I think you want something like CloneZilla or, if you want to get your hands dirty, dd from the command line. Others may have better suggestions.

---

