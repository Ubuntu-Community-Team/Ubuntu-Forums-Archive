---
title: "move /boot from /dev/sda1  to usb drive or to a logical / directory on lvm raid10"
date: 2012-01-16
forum: General Help
---

### Post by bjrnfrdnnd on 2012-01-16
Hello, 

I have the following problem.
My ubuntu box is running on a raid10 system, with 4 harddrives and lvm setup. I have a / partition and a /home partition set up with lvm2. 
When I installed my system, I thought that the /boot directory would be placed on the / partition. However, as I found out right now, for some reason, the /boot partition is the first partition of /dev/sda, and this is also reflected by the /etc/fstab entry. 
My raid system had already 2 disk failures, but luckily not the first one, which, as I said, for some unknown reason has the /boot partition physically on its first partition.
Therefore, losing this first drive would be a pain. 
So I was thinking what I could do to remedy the problem. 

I would prefer to have the /boot directory written to my / partition, so somehow disable the mount /dev/sda1 part and physically copy the /boot directory to my logical volume /. I am not sure how to do that. 

I could also try to get a usb stick and move the /boot directory to the usb stick, and then alter /etc/fstab to reflect that. 

In both cases, I am unsure about the detailed procedure (in particular the grub-install and initramfs things and possible chroots to be done). 

Would be cool if anyone could help me.

---

