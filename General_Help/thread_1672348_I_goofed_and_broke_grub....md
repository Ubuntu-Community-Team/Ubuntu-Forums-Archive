---
title: "I goofed and broke grub..."
date: 2011-01-20
forum: General Help
---

### Post by Karpah on 2011-01-20
OK, so I wanted to try out a Natty daily build so I downloaded the daily CD image, burnt it to a CD, and then used that CD to install onto a USB stick. It worked all well and good.

But in the install process, it did something to grub, so now I can only boot off the USB stick. When I boot without the USB stick plugged in, I get a grub error - device not found <USB UUID here>.

When I do boot off the USB stick, I get a normal grub, with the USB Natty entry, and then my normal 10.10 and Win7 entries. I can still boot into my normal 10.10 install .doing this.

I've tried booting into 10.10, unplugging the USB stick and running sudo update-grub, which I thought would fix the problem but didn't.

Plz help :(

---

### Post by Karpah on 2011-01-21
nobody? :(

---

### Post by Karpah on 2011-01-21
I've worked out that it's booting off the USB stick, the grub menu items I get on boot match what's on the USB stick... I just can't work out *why* it's forcing to boot from there, instead of from my hard drive...

---

### Post by Hippytaff on 2011-01-21
If you boot frim LoveUSB or CD an post the Results.txt by downloading and running the bootscript found [here]("http://sourceforge.net/projects/bootinfoscript/") people will be able to see whats happened.
:-)

---

### Post by oldfred on 2011-01-21
Bootscript will tell us for sure, but Natty must be like Maverick in that it just defaults to install grub to the MBR of sda. When you install you have to do manual install and choose to install grub to the MBR of the the external device.

sudo update-grub just refreshes the menu - grub.cfg. If you boot your install on the USB you can install its grub to the MBR of sdb. Then boot your internal install and install its grub to the MBR of the internal drive - sda.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by Karpah on 2011-01-21
I managed to fix it by reinstalling grub onto my sda drive :) Thanks guys.

---

### Post by Hippytaff on 2011-01-22
Excellent - remember to mark the thread as solved in the thread tools at the top of the page ;-)

---

