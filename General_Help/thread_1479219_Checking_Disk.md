---
title: "Checking Disk"
date: 2010-05-10
forum: General Help
---

### Post by timepilot on 2010-05-10
Sometimes at startup I get this message "Checking disk 1 of 1". Does that mean it's checking all partitions on the hd? :confused:    After a bad shutdown there is no prompt for fsck to run and the system just boots up.  In fstab I have both options set to "1" for the partition Ubuntu is on, all others set to "0".  Any ideas on both? :-k

---

### Post by ajgreeny on 2010-05-10
The system checks the linux filesystem partitions like this every 30 or so boots by default, just to make sure everything is OK.  It will not check any windows file system partitions.

The setting of the number of boot ups before the next check can be changed if you wish with **tune2fs** in terminal, eg, using the command ```
sudo tune2fs -c 60 /dev/sda3
``` would set the default number of checks between file system fsck checks of sda3 to 60.  If you ever have a reason to need a manual check use the command ```
sudo touch /forcefsck
```and at next boot the system will run the fsck for you.

---

### Post by timepilot on 2010-05-10
@ajgreeny

 Thanks for your quick reply and the info! :)

 Is there a way to make the system automatically run fsck after a bad shutdown?

---

### Post by ajgreeny on 2010-05-13
Not that I'm aware of, but I think if there are problems the system will do it automatically with no input from you.  If it does not do it that way, it probably means that the journaling of the linux file systems ext3 and ext4 has done its job as intended.

If you really want to double check just use the touch command I gave last time and quickly restart the system.

---

