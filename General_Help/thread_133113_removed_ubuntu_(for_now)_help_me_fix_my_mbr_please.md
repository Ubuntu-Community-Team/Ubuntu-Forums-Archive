---
title: "removed ubuntu (for now) help me fix my mbr please!!"
date: 2006-02-19
forum: General Help
---

### Post by kenailes on 2006-02-19
was having problesm on my laptop, so I decided that for now I was going to remove ubuntu, go back to jsut windows, and install and a differnt machine for me to learn on--broke a few things with the dual boot, and can't afford the learning curve on my live machine.

I fiugred i could just delete my linux partition, then use knoppix to fix the mbr. so i deleted the partition, and have my knoppix cd, but can't find the doggone command to fix my mbr so I don't get the grub error, any help?

---

### Post by heimo on 2006-02-19
You can do it using Windows install CD:
[http://www.ubuntuforums.org/showpost.php?p=720995&postcount=3](http://www.ubuntuforums.org/showpost.php?p=720995&postcount=3)

---

### Post by kenailes on 2006-02-19
yeah, problem is i don't have a windows install cd. toshiba doesn't provide the windows cd--they only provide a recovery disk taht doesn't allow you to access the recovery utilities

---

### Post by dcstar on 2006-02-19
[QUOTE=kenailes]yeah, problem is i don't have a windows install cd. toshiba doesn't provide the windows cd--they only provide a recovery disk taht doesn't allow you to access the recovery utilities[/QUOTE]
Boot Windows to Safe Mode Command Prompt, then:

fdisk /mbr

---

