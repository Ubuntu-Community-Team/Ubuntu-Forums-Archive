---
title: "Weird Questions: Boot From USB"
date: 2010-02-09
forum: General Help
---

### Post by triggerwicked on 2010-02-09
This may be a bit of an odd question, but I am sure others could benefit from this as well. I want to do a standard 50/50 ubuntu/windows7 install. I am only keeping windows because my wife is not ready to drop it lol.

Basically what I want to do is install ubuntu to the hard drive as normal, but allow windows to handle the MBR so that my wife can just boot the pc as if ubuntu was never there. What would I need to do in order to set my USB stick up to override the mbr and boot into ubuntu. Almost acting as a type of "key" so my wife doesnt have to gripe about Grub.

Thanks for any help on this, I am quite the noob when it comes to anything Linux, but would love to get in and start learning.

---

### Post by snowpine on 2010-02-09
On the last step of the installer, click the Advanced Options button. This will allow you to choose where to install the GRUB bootloader. For example, if your USB drive is /dev/sdb, you can install GRUB there instead of /dev/sda (your internal hard drive).

The only catch is, I am not enough of a Windows expert to tell you whether or not resizing your Windows partition and installing Ubuntu next to it will mess up the Windows bootloader...

---

### Post by triggerwicked on 2010-02-09
awesome, i will give that a try. I guess worst case I can just repair the boot loader with windows. Thanks a ton!

---

### Post by adam814 on 2010-02-09
First defragment your Windows partition.  Some people advise doing it several times.  Then shrink the volume from within Windows.  As long as Windows itself does the resize it shouldn't gripe about it past the first boot.

After you've done that and made sure you can still boot into Windows go ahead and do your install and install GRUB on a USB key as snowpine suggests.  You shouldn't have any trouble with the Windows bootloader as your resize should free up space "after" your Windows partition.

---

### Post by triggerwicked on 2010-02-09
Sounds easy enough, how would you suggest I resize the partition from within windows? Is that an option when booting from the win cd?

---

### Post by triggerwicked on 2010-02-09
Ah nm that last question, didn't know windows 7 had that feature.

---

### Post by Mark Phelps on 2010-02-10
Use the Disk Management utility in Win7 to shrink the OS partition.  Don't use the Ubuntu installer or you'll run the risk of corrupting the Win7 OS and rendering it unbootable.

OH, and before you do this, use the builtin Win7 option to create and burn a Win7 Repair CD.  You might need that to repair the boot loader later if something goes wrong during the dual boot setup.

---

