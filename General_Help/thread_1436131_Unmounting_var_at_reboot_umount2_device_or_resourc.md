---
title: "Unmounting /var at reboot: umount2: device or resource busy"
date: 2010-03-22
forum: General Help
---

### Post by lubosss on 2010-03-22
Hi all,

I'm using Xubuntu 8.04 LTS on LVM partitions. When I'm rebooting/shutdowning the mashine and checking shutdown messages I see:

umount2: Device or resource busy
umount: /dev/mapper/vgsys-lvvar busy - remounted read-only

I put "fuser -m /var  /dev/mapper/vgsys-lvvar" in the init script umountfs but no process is using them.
I would be very thankful if  the message doesn't appear. I found the same problem after lvreducing an LVM device on Read-only archive Ubuntu Forums:
[http://ubuntuforums.org/showthread.php?p=4523671](http://ubuntuforums.org/showthread.php?p=4523671)

Unfortunately, there's no answer :-/
Please, could you advise me if this can be some issue resulting in data loss and if there is some solution for this?

Thanks

---

