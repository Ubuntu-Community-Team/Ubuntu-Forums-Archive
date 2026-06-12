---
title: "Boot probles in Ubuntu 11.10&amp;Windows 7 dual-boot"
date: 2011-11-30
forum: General Help
---

### Post by saivikas on 2011-11-30
I am currently dual-booting windows 7 and ubuntu. Please tell how to customize the boot manager and set the default pointer(priority) to windows 7 in the boot manager (grub).......Thanks in advance!!

---

### Post by maverickaddicted on 2011-11-30
Very Simple Guide -

[http://www.ubuntugeek.com/how-to-set-default-os-when-dual-booting-with-ubuntu-10-10.html](http://www.ubuntugeek.com/how-to-set-default-os-when-dual-booting-with-ubuntu-10-10.html)

OR

Follow this, if you want to see some more information -

[https://help.ubuntu.com/8.04/switching/dualboot-custom.html](https://help.ubuntu.com/8.04/switching/dualboot-custom.html)

---

### Post by Mark Phelps on 2011-11-30
Recommend AGAINST using Startupmanager for 11.10.  It doesn't work well with the newer versions of GRUB.

Instead, use Grub Customizer.  See link below:

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

---

### Post by efflandt on 2011-11-30
Simplest method to default to whichever you booted last is to use gksu gedit or sudo nano to edit /etc/default/grub. Comment out the GRUB_DEFAULT line and add 2 lines like this:

```
#GRUB_DEFAULT=0
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
```Save it and run **sudo update-grub**

After next boot it will default to whatever you booted last previously. So if you last booted Windows it will default to Windows and if you last booted Linux it will default to that Linux kernel.  That way if something wants to reboot for updates to take effect (or reboot from hibernate), it will reboot that OS.  Although, if you did a kernel update you would need to select the new kernel from grub menu once.

---

### Post by saivikas on 2011-11-30
Thanks to all those who replied!!!! I am very lucky that many people are there here to help me in using ubuntu and making the most of it. In the near future, I will try to help others in solving their problems in Ubuntu!!:popcorn::):)

---

