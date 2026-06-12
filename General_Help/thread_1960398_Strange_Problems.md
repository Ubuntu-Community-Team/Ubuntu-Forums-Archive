---
title: "Strange Problems"
date: 2012-04-17
forum: General Help
---

### Post by Boab1993 on 2012-04-17
I am fairly new to ubuntu
 
I built my own computer around a month ago and decided to install ubuntu on a blank hard drive. The hardware was fully compatible but ubuntu was not responding when prompted to start the setup, it just hung. Eventually i found out by trial and error that setting the system in 'nomodeset' for the setup worked and after reading up on how to change startup commands editied the splash in grub2, changing the 'quiet splash' line to 'quiet splash nomodeset'. The computer now runs perfectly on ubuntu 11.10.
 
However im trying to create a multi-boot system with windows XP and the same problem appears to occur with windows, it runs till the setup gets to 'setup is now starting windows'
 
Im wondering if the hardware isnt compatible without driver updates or if there is a way i can change the start-up similar to how i did with ubuntu.
 
Thanks 
 
Hardware;
 
Amd Llano A6-3670K 2.7GHZ(FM1)
Gigabyte GA-A55M-S2V AMD A55(FM1)
Intergrated Radeon 6530D Graphics
500W Power
Viewsonic VW2014wm

---

### Post by 2F4U on 2012-04-17
It is likely that Windows doesn't have the necessary drivers and since it is no longer developed, you may never get them. If you need Windows, it may be an option to run it in a virtual machine.

---

### Post by Mark Phelps on 2012-04-17
This is an FM1 chipset -- which is fairly new -- and Windows XP, especially if you are using an old CD, is unlikely to have the drivers needed for that chipset.

Best thing to do is go to the Gigabyte site, check that make and model motherboard, and see if they have downloadable XP drivers for it.

You may have to write those drivers to CD or USB and use F6 to load those drivers at XP install time.

---

### Post by Boab1993 on 2012-04-18
Thank you for your help.

However i went to the Gigabyte website and the driver format for windows xp is a windows file and wine appears to be bugging out when trying to install them

Any suggestions?

Ive checked wineHq could only find further programs to help install the software, most them failed with 'error code 2'

---

### Post by dino99 on 2012-04-18
> **Boab1993 said:**
> Thank you for your help.

However i went to the Gigabyte website and the driver format for windows xp is a windows file and wine appears to be bugging out when trying to install them

Any suggestions?

Ive checked wineHq could only find further programs to help install the software, most them failed with 'error code 2'

Does not really understand what you mean:
- you does not need wine to install a windows file on XP
- does that mean that XP is an ubuntu guest ?
- ubuntu with the latest kernel should not have issue at all
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

---

### Post by 2F4U on 2012-04-18
> **Boab1993 said:**
> Thank you for your help.

However i went to the Gigabyte website and the driver format for windows xp is a windows file and wine appears to be bugging out when trying to install them

Any suggestions?

Ive checked wineHq could only find further programs to help install the software, most them failed with 'error code 2'

Please read the post from Mark Phelps carfully:

> You may have to write those drivers to CD or USB and use F6 to load those drivers at XP install time.

You must provide the Windows installation with the necessary driver during the install process.

---

### Post by Boab1993 on 2012-04-25
Sorry for the late reply i was out of town for a bit.

Turns out it was the chipset drivers, but i had to install a virtual machine to install it and after that the installation was fine.
Thank you all for your help

Boab1993

---

