---
title: "Issues with RAID0 array after reinstall"
date: 2011-11-10
forum: General Help
---

### Post by Chris_huh on 2011-11-10
I'm trying to set up ubuntu 10.04 on a server which has two 3TB drives in a RAID 0 array. It was all working, but for some reason a week or so back it crashed and I had to reinstall Ubuntu.

But after doing that my RAID array doesn't start up or mount properly. I have set mdadm to auto-start it but when i load ubuntu up it comes back with a status of: Not running, partially assembled. I can then stop the array manually and start again, which does work. (I can then mount it manually too). 

To get it to autostart I've added to mdadm.conf:

DEVICE /dev/sda1 /dev/sdb1
ARRAY /dev/md0 level=raid0 devices=/dev/sda1,/dev/sdb1

i also added something to fstab to automount it, but removed that when i discovered it hadn't even started properly.

Does anyone know what i can do to fix this?

Thanks

---

### Post by Azyx on 2011-11-11
Think I have a similar problems, but raid 1 and PATA-disks. But work after stop and start in disk-utilities. I run 10.04 LTS. I have not edit mdadm.config

[http://ubuntuforums.org/showthread.php?t=1875030](http://ubuntuforums.org/showthread.php?t=1875030)

/Cheers

---

