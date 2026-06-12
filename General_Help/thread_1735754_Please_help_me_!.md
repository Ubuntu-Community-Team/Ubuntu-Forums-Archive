---
title: "Please help me !"
date: 2011-04-21
forum: General Help
---

### Post by Socrat3s on 2011-04-21
:(Ok So I have an acer aspire One netbook. Nothing else installed on it but ubuntu netbook version. I also installed ubuntu using a usb since I have no cd rom. I guess lastnight I didn't shut it down correctly so now when I boot up I get these errors

"mount : mounting /dev on /root/dev/failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory 
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init=bootarg."

(initramfs) 

It gives me a line saying that. Can anyone help as I'm dying because all of my media for my phone is on my netbook.:(

---

### Post by lithopsian on 2011-04-21
Happens all the time and almost always is very easy to fix.  Boot from the USB and run fsck on your hard drives.  Hopefully it will find the errors you left when you didn't shut down properly and fix them.  Then reboot normally.

---

### Post by Socrat3s on 2011-04-21
when I boot from my usb where do I go to find that ?

---

### Post by ajgreeny on 2011-04-21
Open up a terminal and run ```
sudo e2fsck /dev/sda1
```assuming sda1 is the root partition of your ubuntu UNE install.

---

### Post by Socrat3s on 2011-04-21
I got this error when I tried to boot from the usb T___T "No DEFAULT or UI configuration directive found!"
boot:

---

