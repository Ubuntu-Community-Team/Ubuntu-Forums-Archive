---
title: "XP install wiped GRUB boot"
date: 2006-03-25
forum: General Help
---

### Post by sparky100 on 2006-03-25
I installed XP Pro onto a machine with Ubuntu. My Ubuntu partition has been left intact however I am no longer able to boot into Ubuntu.

I have tried using the install cd to re-install grub by choosing the option to manually edit the partition - the partitioner recognises all the partitions when I go to write this i get the error messahe no root filesystem

Booting in rescue mode I have tried grub-install /dev/hda again this gives an error message indicating that no such device exists.

In resuce mode i can still see my data on the linux partition

Hope this makes sense - any suggestions

Simon

---

### Post by izmaelis on 2006-03-25
I had problems with Grub when I tried installing other operating system. [This]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub") guide helped me out. I recovered my Grub by using Ubuntu 5.04 Live CD.

---

### Post by akiro.yamamoto on 2006-03-25
If Ubuntu is the only Linux Version currently installed, you can use
[** THIS !!! **](http://adrian15.raulete.net/grub/tiki-index.php) 
To restore / re-install GRUB.
Hope this info helps ;)

---

### Post by Mustard on 2006-03-25
/me goes to check out the Super Grub disk. :)

---

