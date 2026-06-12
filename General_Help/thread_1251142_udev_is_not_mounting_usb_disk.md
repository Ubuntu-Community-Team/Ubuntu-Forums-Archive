---
title: "udev is not mounting usb disk"
date: 2009-08-27
forum: General Help
---

### Post by Krystanos on 2009-08-27
Hi,

I'm trying to create a backup system, where the computer has a backup on an external disk.
Every week, the disk is changed, in order to protect one backup outside of the building...

So I'm trying to make theses disks to mount in the same directory when I change them.
I try to use udev to do that, but the mount operation is not executed. Here is a rule that works :

```
ACTION=="add", SUBSYSTEMS=="scsi", ATTRS{ieee1394_id}=="0020370200348756:0:0", SYMLINK+="backup", RUN+="/usr/bin/touch /root/udev.begin ; /usr/bin/touch /root/udev.end", OPTIONS="last_rule"
```

The touch commands are well executed.

But when I try to mount the disk with this rule :

```
ACTION=="add", SUBSYSTEMS=="scsi", ATTRS{ieee1394_id}=="0020370200348756:0:0", SYMLINK+="backup", RUN+="/usr/bin/touch /root/udev.begin ; /bin/mount /dev/backup /backup ; /usr/bin/touch /root/udev.end", OPTIONS="last_rule"
```

None of the commands are executed. /backup directory exists and belongs to root. I also tried with "-t auto" option, but it did nothing.

Any hint on why it doesn't work ? Maybe I'm trying the wrong way ?

Thanks for help...

---

