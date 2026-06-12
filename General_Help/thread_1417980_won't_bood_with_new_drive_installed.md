---
title: "won't bood with new drive installed"
date: 2010-02-28
forum: General Help
---

### Post by legolas on 2010-02-28
Hey guys.  I just bought a new Western Digital Caviar Black 1TB SATA disk drive.  I plugged it in and the system wont boot. I get the BusyBox and it says "gave up waiting for root device..."
"...alert /dev/sdc1 does not exist."
When I unplug the new disk drive, it boots up fine.
Any explanations as why it won't boot when I plug it in?
Any help is greatly appreciated.

---

### Post by dcstar on 2010-02-28
> **legolas said:**
> Hey guys.  I just bought a new Western Digital Caviar Black 1TB SATA disk drive.  I plugged it in and the system wont boot. I get the BusyBox and it says "gave up waiting for root device..."
"...alert /dev/sdc1 does not exist."
When I unplug the new disk drive, it boots up fine.
Any explanations as why it won't boot when I plug it in?
Any help is greatly appreciated.

Try swapping the SATA connections on the MB for the two drives.

---

### Post by zarthon on 2010-02-28
Change the order of drives in your BIOS or go into your computer and plug the new drive into a different internal sata connection.
Your new drive is changing the order of your disks so another device, prehaps the new one, is becoming /dev/sdc !

Do you get to GRUB ? 
You can also hack your boot commands in grub and try change it to /dev/sdd1 but then there is your /etc/fstab to contend with etc so your best off just fixing it by either trying different sata prots or, if your bios supports it, change the order of the devices there.

---

### Post by 3rdalbum on 2010-02-28
When you get to Busybox, give it a few more seconds and then type "exit"; you may find that the system will boot.

If this happens, I'd probably suggest reinstalling GRUB.

I've certainly never seen the problem happen after adding a new hard drive.

---

### Post by legolas on 2010-02-28
Yes, I get to the grub menu, but after that it goes to busybox.  I tried changing the boot order in the bios, and I also swapped the SATA positions on the motherboard.  When I type "exit" at busybox it just says the same thing it did before about it gave up waiting and the drive doesn't exist.
Is there something I can try with a live CD?

---

### Post by legolas on 2010-02-28
From the grub boot menu, I hit 'e' to edit and I changed it to boot to 'sda1' and it booted up.  Unfortunately, It didn't stick, the next time I booted the computer, same ol' same ol', it wouldn't boot.  How do I edit the menu to stay- I have heard that you can edit the karmic grub2 grub.cfg, but when it gets updated, it will get written over.

---

### Post by legolas on 2010-03-01
I fixed grub2 using this tutorial on youtube:
[http://www.youtube.com/watch?v=TDf_fRAophc](http://www.youtube.com/watch?v=TDf_fRAophc)
Thanks for your help.

---

