---
title: "Help in installing Ubuntu 5.10 - Partitioning"
date: 2006-03-05
forum: General Help
---

### Post by cslee on 2006-03-05
Hi,

I faced the problem when trying to install ubuntu on a DELL desktop. When it reaches the partioning stage, it does not show any of my harddisk and I was only given the option to "Manually edit Partition table". However, even I go into this option. I do not see any of my harddisks too. 

I had tried to install on another desktop (Compaq) using the same way to create a partion first, then reboot to install and doesnt face this problem. Is there something that I missed out?

Please advice,
Thanks in advance

---

### Post by cotcot on 2006-03-05
Might be a hardware problem. Is it a common make of hard disc ? Is it recognised by other live CD's (maybe you could check it ubuntu live or knoppix or so). Older computer with a new big new hard discs can cause problems. Are you sure about the master/slave connection and the according jumper settings ?

---

### Post by Xian on 2006-03-05
I would surmise that the problem is with Parted (the InstallCD partitioning tool) not being able to properly read your disk due to some partition geometry errors. This will generally not effect cfdisk, fdisk, and other windows applications like acronis and partition magic. It is often caused by some brand of partitioning software not setting the disk geometry correctly during a write session.

Try and run Parted during a linux session (perhaps on a Live CD if you have no HD installation at present), and see if it returns some error messages while reading your disk. You can also go into verbose mode and run 'parted' from the command line while installing by using the Function keys.

---

