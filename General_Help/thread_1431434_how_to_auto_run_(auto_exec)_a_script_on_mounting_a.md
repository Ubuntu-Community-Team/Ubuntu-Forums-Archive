---
title: "how to auto run (auto exec) a script on mounting a device"
date: 2010-03-16
forum: General Help
---

### Post by tanoloco on 2010-03-16
Hello!

The generic question:
I would like to exec a script whenever a user mount a device.
The device could be an internal device (for example a partition on a second hard disk)
or a removable one (for example a usb hard disk).
The script must have sudo capabilities even if the user is not included in the admin group.

Is it possible?

The specific question:
I would like to add acl option to a device whenever it is mounted. 
I tried fstab but it's changing the behaviour of nautilus see:

[http://ubuntuforums.org/showthread.php?t=1414003](http://ubuntuforums.org/showthread.php?t=1414003)

so I would like to create a script with the command
```

sudo mount -o remount,acl /media/data
```and auto execute it any time data is mounted.

Any help?

---

### Post by tanoloco on 2010-03-17
sorry to bother you but I need a help on this :)

Maybe it's not the right place to where post such  question?

Which could be the right one?

---

