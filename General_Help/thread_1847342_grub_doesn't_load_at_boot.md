---
title: "grub doesn't load at boot"
date: 2011-09-20
forum: General Help
---

### Post by grigjd3 on 2011-09-20
Hi everyone, I'm more of an ubuntu utilizer than anything else.  I installed 10.04 as a dual boot on a desktop at work. I selected dual boot option and the partition of the hard drive went fine. However, when I booted up the PC again (without the LiveCD in), it goes straight to Windows XP. Having been through the process a few times, I checked the BIOS output from the bootup and definitely found the partitioned harddrive.  

I tried booting from the live CD and running sudo apt-get install grub and the result is still the same - boots straight to Windows XP. If I were to make a guess, the BIOS is just ignoring the GRUB utility. Is there any help out there for this?

cheers,
grigjd3

---

### Post by rymp on 2011-09-20
Did you try holding shift after the bios screen comes up?

---

### Post by raja.genupula on 2011-09-20
```
sudo update-grub
``` have to do the job .
ok do one thing do this

```
sudo gedit /boot/grub/grub.cfg
```
may be your timeout will be zero there set it to 10 .
so your grub gonna wait for your choice upto 10 sec . 
all the best.

---

### Post by Mark Phelps on 2011-09-20
When you say you installed GRUB, did you install it to its own Linux filesystem partition? Or did you install to the root of the drive?

Installing to a partition would be, for example, to /dev/sda1

Installing to the root of the drive would be, for example, to /dev/sda

Also, do NOT edit grub.cfg (wish folks would STOP making this recommendation!!).  That file gets overwritten every time the grub config file gets regenerated.

---

### Post by raja.genupula on 2011-09-20
> **Mark Phelps said:**
> When you say you installed GRUB, did you install it to its own Linux filesystem partition? Or did you install to the root of the drive?

Installing to a partition would be, for example, to /dev/sda1

Installing to the root of the drive would be, for example, to /dev/sda

Also, do NOT edit grub.cfg (wish folks would STOP making this recommendation!!).  That file gets overwritten every time the grub config file gets regenerated.


yeah i think we can make that by making as 
```
sudo dpkg-reconfigure grub-pc
``` 
we can make the grub to /dev/sda
by choosing at the options while re configuring Grub.

---

