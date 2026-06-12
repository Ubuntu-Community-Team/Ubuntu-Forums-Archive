---
title: "Issue with CD drive"
date: 2010-05-03
forum: General Help
---

### Post by anilv_4 on 2010-05-03
Hi,
I am new to the Ubuntu Forums. Not sure if this question belongs here or elsewhere. I have recently installed Ubuntu 8.10 on my Dell Laptop and the installation went fine. I could boot up and all but I noticed that the CD drive became completely unresponsive right from the time I booted into Ubuntu. I had restarted multiple times and the problem persists, the drive just does not open up at all. It was working perfectly fine before the installation (on XP). Following is the output of gedit sudo /etc/fstab command:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7a0abb86-b663-487f-9476-7286305aa25d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=d76a3b62-a00e-473a-8f80-8272324e2eb5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

Can someone please help me resove this issue.

Thanks

---

### Post by anilv_4 on 2010-05-03
Can someone please help me resolve this issue. I dont want to go back to windows XP.

---

