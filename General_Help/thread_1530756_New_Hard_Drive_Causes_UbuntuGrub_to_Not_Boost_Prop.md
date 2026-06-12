---
title: "New Hard Drive Causes Ubuntu/Grub to Not Boost Properly"
date: 2010-07-14
forum: General Help
---

### Post by gspira on 2010-07-14
I installed a new hard drive and "lost" Ubuntu (the latest) on a windows vista system  I now get sent to a grub command line that's similar to a bash environment.  I never get to the usual grub 2.0 list of versions I can choose from. I have no clue where to go from here.  The ubuntu directory is still on the same hard drive, but obviously the new hard drive has "moved" its location in a non-physical sense so that it doesn't boot up properly.  Anyone have any ideas?


Thanks for any help in advance.

Greg

---

### Post by DjSesso on 2010-07-14
Do you still have the old drive and its working?

---

### Post by maxpathan on 2010-07-14
Have you REPLACED your drive or added an extra one?

We had a similar problem on a RED HAT machine. We plugged in a 1TB USB drive. After shutdown, the computer would not boot. It seemed like a GRUB problem. I was about to re-install, but unplugged the USB Hard drive and rebooted. That solved the problem.

Regards
Max

---

### Post by gspira on 2010-07-16
I added s 1 TB internal drive.  I also removed several external usb drives, but for various reasons I don't think they have anything to do with the problem here.  I did this to upgrade to Windows 7, with which I did a fresh install on the new drive which is now c (the problems started when i installed the drive before i installed win 7 and before it turned into a bootable c drive).  The original Vista drive remains bootable in that operating system.  But the 3rd drive, the linux drive, will not boot properly; the computer can't even get into grub properly when I direct it to Linux; it just throws me to the grub command line, which seems pretty useless.  I can't even quit or exit from it; I have to reboot the computer by pressing the power button to get out of there.

Greg

---

