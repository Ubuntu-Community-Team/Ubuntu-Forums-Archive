---
title: "Question about dual boot and multiple HDDs"
date: 2011-07-13
forum: General Help
---

### Post by redfox1160 on 2011-07-13
I was wondering if it was possible to install another HDD in my computer and have the option to dual boot. Could I install the HDD then install Ubuntu to it? Or would I have to do a RAID setup or something so that it looks like one large volume (then partition it accordingly)? Thanks!

---

### Post by seawolf167 on 2011-07-13
Sure - plug the drive it, turn it on in BIOS (if applicable), boot off your Ubuntu LiveCD, and select to install to your new disk. I suggest at least separate /home and / (root) partitions on that drive, and make sure not to overwrite the Windows loader with Grub. If you are worried about screwing something up, you can always unplug the Windows drive before you start then configure Grub afterwords. 

[Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is a how-to guide for Windows & Ubuntu dual booting.

P.S. backups are always a good idea - I suggest making one with [Clonezilla ]("http://www.clonezilla.org")before you start

---

### Post by redfox1160 on 2011-07-13
> **seawolf167 said:**
> Sure - plug the drive it, turn it on in BIOS (if applicable), boot off your Ubuntu LiveCD, and select to install to your new disk. I suggest at least separate /home and / (root) partitions on that drive, and make sure not to overwrite the Windows loader with Grub. If you are worried about screwing something up, you can always unplug the Windows drive before you start then configure Grub afterwords. 

[Here ]("https://help.ubuntu.com/community/WindowsDualBoot")is a how-to guide for Windows & Ubuntu dual booting.

P.S. backups are always a good idea - I suggest making one with [Clonezilla ]("http://www.clonezilla.org")before you start

Will I have to change what drive it is booting from by using the BIOS each time, or will it set up GRUB automatically?

---

### Post by sanderd17 on 2011-07-13
You have to think about what disk is your primary disk in the bios settings.

If you take your new disk as your primary, than you have to install the ubuntu bootloader to there. This will leave the Windows MBR intact, and you will be able to choose between windows and Ubuntu at boot time. If you remove the Ubuntu HDD, windows will still work. (so I would take this option)

If you take the old disk as your primary disk, than you have to install the MBR to the old windows disk. That means when you remove the new Hdd, the old windows installation won't work either. But if both hdds are present, there is no difference from the first installation.

---

### Post by redfox1160 on 2011-07-13
> **sanderd17 said:**
> You have to think about what disk is your primary disk in the bios settings.

If you take your new disk as your primary, than you have to install the ubuntu bootloader to there. This will leave the Windows MBR intact, and you will be able to choose between windows and Ubuntu at boot time. If you remove the Ubuntu HDD, windows will still work. (so I would take this option)

If you take the old disk as your primary disk, than you have to install the MBR to the old windows disk. That means when you remove the new Hdd, the old windows installation won't work either. But if both hdds are present, there is no difference from the first installation.

Okay, that makes sense. Will the setup work the same as when I'm installing it on 1 HDD?

---

### Post by sanderd17 on 2011-07-14
> **redfox1160 said:**
> Okay, that makes sense. Will the setup work the same as when I'm installing it on 1 HDD?

If you install both OS on one HDD, than you will have to shrink the Windows partition (with a windows tool or with the Ubuntu installer) and install the Linux bootloader to it. This is done automatically by the installer if only one disk is found.

---

