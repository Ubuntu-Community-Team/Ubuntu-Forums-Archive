---
title: "Uninstall Ubuntu"
date: 2010-11-23
forum: General Help
---

### Post by mmvincent1 on 2010-11-23
Hi, I am new to Ubuntu and have installed it on a laptop because I did not have my Vista/System recovery CD's. Wanted to see if lap Top was OK before ordering recovery CD's from HP.
Now I have Ubuntu (none dual) and need to remove it and re-install my original system. Could not get my wireless network to work. 
CD Rom does not recognize boot files. 
 
Ubuntu is nice and if I had the time I would surely play with it until I got it right but I need to restore the laptop to original condition because I will send it to my Dad (never used a computer) in Germany for Christmas. I can support Windows over the phone but not Ubumtu.
 
Please help!
 
Regards
 
Mary Vincent

---

### Post by dark.generic on 2010-11-23
What laptop is it?

Is there a recovery option on boot?

---

### Post by matt_symes on 2010-11-23
Hi

> CDRom does not recognize boot files. 

What do you mean by this? 

Is the CRom set as the first boot device in the BIOS. How did you install Ubuntu? From CD, USB ?

For future reference, you can check the hardware from the LiveCD.

It should just be a case of getting a recovery CD and booting into that.

Kind regards

---

### Post by mmvincent1 on 2010-11-23
I have not uninstalled it yet. Have Vista boot CD but system will always boot to Ubuntu Log On.
 
Boot sequence is set to (1) CD, (2) HD

---

### Post by mmvincent1 on 2010-11-23
> **dark.generic said:**
> What laptop is it?
 
Is there a recovery option on boot?
 
 
HP 2500 series 
Vista OS
 
Yes, recovery F11 but will only boot right back to Ubuntu log on

---

### Post by WorMzy on 2010-11-23
Put in the Ubuntu CD or USB you installed Ubuntu with, and boot from it. When asked whether you want to install or try Ubuntu, choose "try". Once it's finished loading up the desktop environment, press Alt+F2, and run "gksu gparted". Once gparted has loaded, right-click on the partition and choose "Delete". If you have a swap partition, you may need to right-click it and choose "Swapoff" before you can delete it. Once you have marked all the partitions for deletion, click "Apply". Reboot, put in the Windows disk, boot from it, and follow the install procedure.

---

### Post by matt_symes on 2010-11-23
Hi

Can you set (2) HD to none in the BIOS and reboot?

Kind regards

---

