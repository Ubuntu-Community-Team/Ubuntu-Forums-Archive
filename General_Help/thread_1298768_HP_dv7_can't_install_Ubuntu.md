---
title: "HP dv7 can't install Ubuntu"
date: 2009-10-23
forum: General Help
---

### Post by Gluck on 2009-10-23
Good day to you all,
I really need your help in the following problem:
I've got HPdv7(amd64) where was installed vista by manufacturer. Recently, because of installed program the OS system has completely crashed. Actually, I really didn't like Vista therefore decided to install Ubuntu. I downloaded (on other laptop) Ubuntu Iso file from the official webpage and tried to burn it on the disc, but I was failed. Then I tried to create bootable USB flash drive on the same laptop. I followed to tutorial which is showed at [http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/](http://www.pendrivelinux.com/usb-ubuntu-904-persistent-install-windows/), but when started installing Ubuntu from the usb drive on HP, then again was fail. I've tried other ways in assistance with UNetbootin, too. But with the same result. There is always the same message pops-up:

...Could not load /lib/modules/2.6.28-11-generic/modules. dep...
Please, help me with advise how can I install Ubuntu on my HP dv7(amd64)?
Thanks in advance for any reply.

---

### Post by screaminfakah on 2009-10-23
If windows crashed and was not shut down properly the partition its on may still be mounted.  
Pop in the Ubuntu CD and select try Ubuntu.  It will load a live session. Open a terminal and type
```
sudo apt-get install gparted
```
after install open gparted and select the Windows partition and see if it is still mounted.  If it is you may be able to unmount with gparted.
Or you could use gparted to format the drive.

---

