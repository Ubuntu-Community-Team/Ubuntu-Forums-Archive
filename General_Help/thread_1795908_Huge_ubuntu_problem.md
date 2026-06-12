---
title: "Huge ubuntu problem"
date: 2011-07-03
forum: General Help
---

### Post by aeroic on 2011-07-03
I recently downloaded and installed Ubuntu, on a different partition on my hard drive, I decided that it was not for me, and going back to Windows 7 using Grub, I deleted the partition that it was on and merged it back into my main hard drive. I turned my computer off for the night and when I turned it back on it went into Grub Rescue mode, so I cannot boot into windows. Any options of system recovery on my boot menu all route to the Grub rescue boot menu. I need help fast as I dont want to have to wipe my hard drive and buy another copy of Windows 7.

Please Help!

Aeroic

---

### Post by gandaran on 2011-07-03
you just have to fix the windows boot loader, you can do that with the windows disk or download the rescatux tool.
[http://www.supergrubdisk.org/category/download/rescatuxdownloads/](http://www.supergrubdisk.org/category/download/rescatuxdownloads/)

---

### Post by aeroic on 2011-07-03
How do I use that tool? Do I burn it to a disk using another computer?

---

### Post by gandaran on 2011-07-03
> **aeroic said:**
> How do I use that tool? Do I burn it to a disk using another computer?
yes, burn the ISO to a cd (with image burning tool) then boot the cd, choose the repair windows option to remove grub and fix the windows boot.

---

### Post by aeroic on 2011-07-03
I got everything restored, but for the computer to boot, I am going to need the installation disk, of which i do not have. Thank you for your help. :)

---

### Post by aeroic on 2011-07-03
A quick question, to all those who read the OP and all reply's, can I use the CD I originally installed Ubuntu onto, to re-install it using the alongside windows option, and use the GRUB 2 option to re-boot windows? If it wont work, It would be fine to use Ubuntu for the time being. But will it harm/delete my windows files?

---

### Post by prodigy_ on 2011-07-03
You don't need Linux installed to chainload-boot Windows from Grub (though you still need Grub to be installed somewhere). Read [this HOWTO](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2) about reinstalling Grub2 from LiveCD.

But if you're not planning to use Linux at all, I'd suggest to look [here](http://neosmart.net/blog/2009/windows-7-system-repair-discs/). From a recovery disk you can just replace Grub with Windows bootloader.

---

### Post by aeroic on 2011-07-04
I'ts not that I don't want to use Ubuntu, and I'm not too worried about windows, but its just my personal files I need. I have an external hard drive, can i load Ubuntu, using the install side by windows, and move all my personal files to my external HDD, or will it not work? I cannot do anything with my PC, even those recovery disks come up with the same message of Windows Boot Manager, also, on that screen it gives a code of 0x000000e, does that mean anything?

---

