---
title: "Ubuntu 11.10 to Lubunto 11.10?"
date: 2011-12-30
forum: General Help
---

### Post by davidafranklin on 2011-12-30
Hello,

I have a very old machine (Compaq Presario 700Z 1.4Ghz, 256MB RAM) that has a dual boot Win XP and Ubuntu 11.10. I want to install Lubuntu 11.10 because of its lighweight and at the same time delete completely Windows XP to gain drive space and also remove Ubuntu (too heavy to run on this machine).

What is the best way to install? From Windows with pendrive linux/Wubi or from Ubuntu (not sure how to do it from Ubuntu)?

Note that my CD rom does not work and I cannot boot from a USB..

Thanks

---

### Post by Rex Bouwense on 2011-12-30
If I read your post correctly, you want to install Lubuntu but your CD drive does not work and you cannot boot from a flash drive.  I would say that you are up the proverbial creek.  The easiest way to install is use the whole hard drive,  however you cannot boot from either the CD or flash drive.  Can you borrow an external CD drive from a friend?

---

### Post by davidafranklin on 2011-12-30
Even an external drive would not be recognized by my bios.

I can log to Ubuntu or Win XP. Once in one of these 2 OS, I can do everything (network, use USB, internet connection..).

---

### Post by lolpenguin on 2011-12-30
If you boot from GRUB then you can do this, but if you are using the Windows bootloader, then you'll need to set the default to GRUB or you won't be able to boot.
Delete Windows
**_Make sure there is nothing you need on your Windows partition_**, and delete it using your favourite partition editor. Then expand your Ubuntu partition as much as you want.
Install Lubuntu 11.10
Make sure you've backed up anything you need to keep.
Run in a terminal (suggest using a teletype):
```
sudo apt-get install lubuntu-desktop
```
to install all Lubuntu components you would get in a normal install. Then
```
sudo apt-get remove ubuntu-desktop
```
This will remove all of the Unity/GNOME bits you don't want.

---

### Post by davidafranklin on 2011-12-30
Sorry, I lost you on this one. I am not familiar with the "GRUB".

Right now I can select my OS when I boot. I just do not know how to install lubuntu. Once this is don e, I think I can remove useless partitions but not sure how to install.
I have used WUBI with a lubuntu ISO File but once I install, it is Ubuntu 12.04 tyat shows up which does not make sense.
Should I go to the "minimal version" of Lubuntu?

I am open to any other light distro but it seems that other ones like puppylinux only work from a live cd or USB boot which my BIOS does not allow.

---

### Post by chipbuster on 2011-12-30
Are you sure your BIOS doesn't allow this? I'm pretty sure that almost every BIOS has an option for booting off of [not the main hard drive] in it somewhere.

---

### Post by davidafranklin on 2011-12-30
Unfortunately it cannot, this laptop is almost 10 years old, USB was not very spread out at that time. Even the mouse was not USB per default so you have an idea of the dinosaur...
My only options are floppy, HDD, Disc (Does not work) and network.

---

### Post by Rex Bouwense on 2011-12-30
Does your computer have a USB slot?  If it does insert a flash drive and then reboot.  Go to your BIOS and look under hard drive.  Many computers recognize a flash drive as another hard drive.  My old Dell Inspiron 1000 does that and so does my netbook, which is only a couple of years old.  If it recognizes the flash drive you can configure your computer to boot from the flash drive which it thinks is another hard drive.  Create a bootable flash drive,  You will need a one Gb flash drive to do this.

---

### Post by davidafranklin on 2011-12-30
Tried that, No 2nd HDD appears, just the normal one in addition to floppy, CD and Network.

---

### Post by mörgæs on 2011-12-30
If you have access to another computer, you can move the harddisk and do the install here. After that you just move the harddisk back.

---

### Post by elliotn on 2011-12-30
correct me if I am wrong but you said you.already have ubuntu installed? if so you don't need cd or staff you just have to install lubuntu-desktop as mentioned in one of the above post, your ubuntu will be made into lubuntu.

---

### Post by davidafranklin on 2011-12-30
Not really an option at this time, So I guess there is now way to install Lubuntu from Linux or from Windows without going thru the install  boot, right?
Any other suggestion regarding very light distros that can be installed from Linux or Win XP?
Thanks

---

### Post by dRounse on 2011-12-31
> **elliotn said:**
> correct me if I am wrong but you said you.already have ubuntu installed? if so you don't need cd or staff you just have to install lubuntu-desktop as mentioned in one of the above post, your ubuntu will be made into lubuntu.

I would do that or go into your BIOS like mentioned above and there should be your flash drive where your floppy is you just have to switch them, thats what i did on my computer that sounds just like yours. Or just remove the ubuntu desktop and install the lubuntu desktop. Then run gparted and erase the XP partion

---

### Post by mörgæs on 2011-12-31
With PLOP you can install from a floppy.

[http://www.plop.at/de/bootmanager.html](http://www.plop.at/de/bootmanager.html)

---

### Post by SLEEPER_V on 2011-12-31
[http://www.laptoprepair101.com/laptop/2007/04/17/access-hard-drive-using-usb-enclosure/](http://www.laptoprepair101.com/laptop/2007/04/17/access-hard-drive-using-usb-enclosure/)

you can pull your hard drive from your laptop, use the tool above, and attach it to a pc that can boot from a cd or usb.  Then you boot into the lubuntu disc/usb and choose to install to the drive that the laptop hdd is attached to.

I had the same issue with and old laptop, where the manufacturer basically didnt allow the pc to boot from any alternative source, so i had to use this method

---

### Post by rjf1 on 2011-12-31
Since you already have ubuntu installed, as someone suggested earlier, from your ubuntu installation, open a terminal and just do 'sudo apt-get install lubuntu-desktop'; logout; login under lubuntu; do 'sudo apt-get remove ubuntu-desktop'

Problem solved.

---

### Post by davidafranklin on 2011-12-31
Thanks all!

---

