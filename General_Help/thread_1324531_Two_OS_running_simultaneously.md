---
title: "Two OS running simultaneously?"
date: 2009-11-12
forum: General Help
---

### Post by ibates on 2009-11-12
Can anyone suggest a good methodology for running Ubuntu 9.10 and Windows XP SP3 simultaneously?

I would like to be able to switch OS by a simple toggle without having to reboot each time I want to go back and do something which runs only on Windows XP.  (I am moving away from Windows, but there are still some applications I need which are not able to run on Ubuntu (yet)).

I am running Ubuntu 9.10 on its own HDD and Windows on another HDD.  The machine is an ASUS P5VD2-X with Intel Core Duo CPU.  4GB RAM.  Generic Network operates continuously.

Any assistance in sorting out what works and what doesn't would be greatly appreciated.

---

### Post by prem1er on 2009-11-12
Run Windows inside a virtual machine on Ubunutu.

---

### Post by coffeecat on 2009-11-12
> **prem1er said:**
> Run Windows inside a virtual machine on Ubunutu.

+1 to that. The best way.

Have a look here:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

If you want to try VirtualBox, use the latest 3.0.10 version from there, not the ose one in the Universe repository.

---

### Post by Tiganjero on 2009-11-12
I had really good experience with VirtualBox, especially when they added the Guest Addons. I suggest you install it and see if it suits you. Even though I ran Ubuntu, with XP in VirtualBox, and had a server that included a lot of needy programs, I was able to do everything else normally with only 2GB of RAM, after upgrading, it was even better.
```
sudo apt-get install virtualbox-3.0
```

EDIT:
> If you want to try VirtualBox, use the latest 3.0.10 version from there, not the ose one in the Universe repository.
After you install it with the command I posted, it will update it self. Though it doesn't matter :)

Cheers,
George

---

### Post by steviefordi on 2009-11-12
Virtualization is definitely the way to go.

Virtualbox worked for me for a while, then after an update from the vb repository, usb passthrough seemed to stop. I later found out it's only available in the proprietary upgrade. The only reason I was using a virtual machine was to run XP for two devices that connected via USB. It is now useless to me.

I'm probably going to give Qemu a go. Not sure if usb passthrough is available but given Qemu is completely open it probably is.

---

### Post by ibates on 2009-11-12
Thanks for that.  I will give it a go.

---

### Post by OSX@Linux on 2009-11-12
Are you currently dual booting? If so, take a look at the user manual for Virtualbox. You have to create a special .vdi file so it can access the physical hard disk. It;'s a really simple process, just one command. 

"VBoxManage internalcommands createrawvmdk -filename /home/yourhomedirectory <insertoutputfilehere.vdi> -rawdisk /dev/sda(partition #) -register"

You can find the partition number in Gparted or partition editor. It will be /dev/sda# where # is the partition number. 

Have fun

---

### Post by OSX@Linux on 2009-11-12
Are you currently dual booting? If so, take a look at the user manual for Virtualbox. You have to create a special .vdi file so it can access the physical hard disk. It;'s a really simple process, just one command. 

"VBoxManage internalcommands createrawvmdk -filename /home/yourhomedirectory <insertoutputfilehere.vdi> -rawdisk /dev/sda# -register"

You can find the partition number in Gparted or partition editor. It will be /dev/sda# where # is the partition number. 

Have fun

---

### Post by andrew.46 on 2009-11-12
Hi ibates,

Why stop at only 2? Perhaps this is as good a time as any to demonstrate my own setup with Slackware 13.0 host and guests of Hardy Heron, Karmic Koala and Windows XP. And could I put a plug in here for the OSE edition which will fill all of your needs *except* usb while remaining* completely* Open Source. 

All the best,

Andrew

---

