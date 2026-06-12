---
title: "/dev/mapper/cryptswap1 problem"
date: 2012-10-06
forum: General Help
---

### Post by whatthefunk on 2012-10-06
When I boot up, I get a message on the spalsh screen saying "/dev/mapper/cryptswap1 is not ready yet or not present"  I can manually turn swap on, but on boot I still get the error message.  Currently, my home partition is not encrypted, but it used to be...maybe thats part of the issue??   What can I do about this?

---

### Post by flectron on 2012-10-06
Im having the same issue, but Ubuntu seems to fully work without it  ):P

---

### Post by whatthefunk on 2012-10-06
I think I figured it out. 
First, I commented out the swap line in /etc/crypttab  
Then I used the output of "sudo blkid" to find the UUID of the swap partition.
I made a new swap file in the partition with "sudo mkswap /dev/sdax" where x is the partition number.
I then updated the /etc/initramfs-tools/conf.d/resume file to show the correct swap UUID.
Updated initramfs with "sudo update-initramfs -u"
Reboot
No message and "free" shows a usable swap partition.

---

