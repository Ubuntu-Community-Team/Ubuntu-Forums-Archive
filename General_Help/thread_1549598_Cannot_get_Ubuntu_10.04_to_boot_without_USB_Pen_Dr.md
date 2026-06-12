---
title: "Cannot get Ubuntu 10.04 to boot without USB Pen Drive"
date: 2010-08-10
forum: General Help
---

### Post by xsound on 2010-08-10
I installed Ubuntu 10.04 on a HP Mini 5102 using a bootable USB drive, but if I try to boot the machine without this USB, an error appears saying: Non-System Disk or Disk Error

When I insert the USB, everything works fine. I check the USB flags using GParted, and it has the bootable flag set. On the other hand, the hard drive in the computer has no flags set.

Please, help me. Thanks in advance.

---

### Post by sikander3786 on 2010-08-10
Hi.

Did you try setting bootable flag for HDD in gparted?

Boot from the live USB, set HDD flag as bootable and reboot. If this doesn't solve the problem, you might have to reinstall GRUB.

Post back.

Regards.

---

### Post by xsound on 2010-08-10
Thanks for the reply. I tried making the ext4 partition inside the HDD bootable, but when I restart the machine, it keeps rebooting repeatedly.

---

### Post by yunone on 2010-08-10
that has happened to me in the past. What i have done is just start over with the USB drive. Something didnt go quite right or install right and is now having difficulty. 

I would start over
make sure everything is updated from synaptic
reboot and use the drive a couple cycles
then start using it and configuring for everyday use if it boots right


sometimes the usb installs just dont work right. i cant count how many times with how many distro's i have tried and failed at or didnt like with the usb install.



another thing to try is installing 9.10 to the usb drive and see if that works for a day or two after you do all the system updates. 10.04 for me is buggy and not the smoothest, but everyone has diffferent experiences :)

---

### Post by xsound on 2010-08-10
I have installed both 10.04 desktop edition and netbook edition several times, and they always do the same thing.

I also installed 9.10 and it works perfectly. The problem is that both the wireless and Ethernet adapters do not work.

---

### Post by yunone on 2010-08-10
are you running the latest version of the HP BIOS? i know its a random question, just want to make sure.


When you start talking about Network devices and them not working, it comes down to a driver issue. just have to get the driver on the device somehow and get it installed.

With a fresh install of 9.10 on my Dell D620 the wireless card wont work until i run Update manager and get the latest updates on the computer and then it works fine.

---

### Post by schwabdale on 2010-08-10
Sounds like you installed Grub to the USB drive. 

During the install you need to specify where to install grub.

---

### Post by xsound on 2010-08-10
How can I get GRUB installed on the machine itself? I did not see any options during installation to specify the location of GRUB

---

### Post by xsound on 2010-08-11
Yep... I was making the USB drive a bootable drive, instead of making the main drive the bootable one. 

I clicked on the advance button, on the last part of the installation. 

Thanks for your help!!!

---

### Post by schwabdale on 2010-08-11
> **xsound said:**
> Yep... I was making the USB drive a bootable drive, instead of making the main drive the bootable one. 

I clicked on the advance button, on the last part of the installation. 

Thanks for your help!!!


During the install you have the option to specify the partitions manually. Select this option. After you tell it which drive to install to... hit next. When you get to the advanced button you are referring to, this is where you tell it where you want to install Grub. 

If you install Grub to the USB, it will only boot when the USB is installed. 

So... if you want to move the USB from PC to PC, you would install Grub to the USB. If not, you need to install it to the Hard Drive. 

To find out which drive is which,, hit Alt+F2 and type Xterm. 
Next, type sudo fdisk -l

This will list your drives and partitions. If you hard drive is SDA, you need to install it to SDA, not SDA1.

---

