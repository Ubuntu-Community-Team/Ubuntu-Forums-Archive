---
title: "System Wont boot when new HDD is plugged in"
date: 2010-05-22
forum: General Help
---

### Post by rugbert on 2010-05-22
So I just got a new 1gig HDD and added it to my ubuntu server but if the HDD is plugged in when the computer is off, it will not boot. But if I turn it on and then plug it in, everything is fine.

I dont know whats happening when it tries too, there is no monitor. What logs should I check and what should I look for?

---

### Post by arrange on 2010-05-22
I'd look at */var/log/syslog* and compare the output with and without the HDD, and also when the HDD is plugged in when the computer is on.

---

### Post by jamesisin on 2010-05-22
If you attached a new hard drive you may be moving your boot drive from its previous location (sda becomes sdb for instance).  Take a look in your /etc/fstab file to ensure that the boot drive is called out using its UUID instead.

---

### Post by jinba.ittai on 2010-05-22
Try going into you BIOS and setting which hard drive you want it to boot from.

---

### Post by oldfred on 2010-05-22
On my machine the drive order is the order they are plugged into the SATA ports. But mixed IDE and SATA sometimes the IDEs become the first drives.

Also check your /boot/grub/device.map

---

