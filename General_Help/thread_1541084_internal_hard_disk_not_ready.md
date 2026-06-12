---
title: "internal hard disk not ready ?"
date: 2010-07-28
forum: General Help
---

### Post by worksofcraft on 2010-07-28
When I boot my computer, seemingly at random I get:

"The disk drive for /home is not ready yet or not present"
"Continue to wait; or press S to skip mounting or M for manual recovery."

Waiting doesn't help, but simply rebooting and trying again does.

Anyone have any ideas what could be causing this ?

---

### Post by prodigy_ on 2010-07-28
You might want to read [this thread](http://ubuntuforums.org/showthread.php?t=1466555) and try the solution from there.

If it won't help, open terminal and run the following commands: ```
cat /etc/fstab
sudo blkid
```
and post the output here.

---

### Post by worksofcraft on 2010-07-28
I copied the uuid from ls -l /dev/disk/by-uuid
and replaced /dev/sda4 with UUID=... in /etc/fstab.


Reboot worked fine, so thanks :)
It looks like that may have solved the problem !

The strange thing is that it only sometimes failed before, so I'll post if it happens again and leave this thread open for a moment yet. In theory fstab should be working consistently either way.

---

### Post by prodigy_ on 2010-07-28
> **worksofcraft said:**
> In theory fstab should be working consistently either way.
You're right but for many reasons UUIDs are recommended over /dev/sdXX. UUIDs are unambiguous and generally more reliable.

---

