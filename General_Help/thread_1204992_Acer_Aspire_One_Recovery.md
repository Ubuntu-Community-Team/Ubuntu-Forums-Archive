---
title: "Acer Aspire One Recovery"
date: 2009-07-05
forum: General Help
---

### Post by Marfish on 2009-07-05
K, so I was trying to recover my original system after installing the Ubuntu 9.04 netbook edition. I had wanted to recover the original so I could then put the netbook edition of ubuntu on the other harddrive and have the choice on startup. Unfortunately, I'm having a hell of a time getting the original system back on there. So I want to the trouble of buying an external cd drive and am finding that even once the recovery is finished, it still starts up with a grub loader messege from the netbook ubuntu,telling me it has an error 17. Even when I tried to install the netbook edition back on it, it was not able to install the grub boot loader. What do I do, I am getting seriouslly frustrated with this, and the acer support never got back to me. Any help will be greatly appreciated.

---

### Post by .nedberg on 2009-07-05
I guess you are restoring Windows? You will need to restore the MBR.

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

If you don't have a WinXP cd then I don't know how to do it, sorry! Perhaps Ultimate Boot CD will do it?

---

### Post by dhughes on 2009-07-05
Perhaps you can boot from a USB flashdrive with the UNR image on it (like you did when you installed it...didn't you?) and choose gparted, delete the partition and then create a new FAT32 or NTFS partition, then try reinstalling Windows.

---

### Post by Marfish on 2009-07-05
K, I looked into the MBR and it seems that linux erased it. So, I also looked into whether the recovery disks had the option to restore it. It did not. It has the option to restore to the factory default, but this seems to not restore the MBR. So, how do I either use the grub to load my software, or recover the MBR?

---

### Post by .nedberg on 2009-07-06
I think the easiest way would be to get a Windows CD, anything newer than 98 will do, and boot into recovery console with an external CD-ROM. The follow the instructions I gave above.

If this is not an option then you could try with FreeDOS and a USB-stick. I found this how-to describing how to make a stick with FreeDOS. [http://wiki.fdos.org/Installation/BootDiskCreateUSB](http://wiki.fdos.org/Installation/BootDiskCreateUSB)

---

