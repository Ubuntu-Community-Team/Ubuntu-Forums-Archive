---
title: "Grub no such disk"
date: 2010-03-15
forum: General Help
---

### Post by uknapster on 2010-03-15
i have a acer laptop with windows 7, & Ubuntu 9.10 on dual boot, i also installed Ubuntu 9.10 on a USB memory stick, now if i start the laptop up with out the memory stick plugged in i get. I start the laptop, you see the bios acer screen and then.
 
GRUB. no such disk

thank you in advance

---

### Post by l4zy on 2010-03-15
Did you install your Ubuntu 9.10 into USB-stick or hdd + usb-stick ?

If u are using grub you need to boot up with Live-CD. Then open a terminal and use grub and determine where your /boot is. 

Remember to mount your disk before doing this =)

If you are using grub2 it's a bit different.

Boot up with live-cd, mount right disk to /mnt or where you want it to be mounted.

Then you need to tell grub to write the right locations of boot files.

it's something like this: 

grub-install --root-directory=/mnt/ /dev/sd*

ofc it depends where you have the files and so on...

---

### Post by uknapster on 2010-03-15
Thank you for your fast reply, this is the really error message. 
Grub loading
error: no such disk
grub error

I have ubuntu on inernal hard drive and USB data stick, so I could carry a copy with me

---

### Post by ajgreeny on 2010-03-15
When you installed ubuntu to the memory stick it will probably have put grub from that install onto the MBR on sda, assuming there is only one hard disk.  That grub will then point to the memrory stick install for the grub config files, and when the usb stick is not attached it will, of course, fail.

The simplest way out of this is to attach the memory stick, boot to your hard disk version of ubuntu, not the usb version, and then use the command ```
sudo grub-install /dev/sda
```.  You will then, possibly need to run ```
sudo update-grub
```just to be sure everything is correct in the hard disk grub.cfg file, which will now be used for booting the machine.

---

