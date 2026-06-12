---
title: "livecd-iso-to-disk.sh"
date: 2011-03-01
forum: General Help
---

### Post by Rodayo on 2011-03-01
Right so I'm using a script called livecd-iso-to-disk.sh script to create a bootable usb. The sript isn't important though.

Now in the arguments you're supposed to indicate a partition name. But my usb drive gets auto-mounted to /media. And if I try to pass in /dev/sdb it gives me a "no media detected" message.

What do?

---

### Post by Smart Viking on 2011-03-01
/dev/sdb is the device name, not the partition name. If there is only one partition on the drive then the correct partition name will be /dev/sdb1

---

### Post by Rodayo on 2011-03-02
> **Smart Viking said:**
> /dev/sdb is the device name, not the partition name. If there is only one partition on the drive then the correct partition name will be /dev/sdb1

Sorry I meant the partition name =P

And I solved the problem. It was /dev/sdc

Thanks anyways =]

---

