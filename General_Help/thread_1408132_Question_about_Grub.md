---
title: "Question about Grub"
date: 2010-02-16
forum: General Help
---

### Post by TheRevTastic on 2010-02-16
Is there anyway to make it so I don't have to use it? And just use the regular one which shows what Os's to choose from, like on most Windows machines when you dual boot etc?

---

### Post by djchandler on 2010-02-16
> **TheRevTastic said:**
> Is there anyway to make it so I don't have to use it? And just use the regular one which shows what Os's to choose from, like on most Windows machines when you dual boot etc?

If you install Ubuntu with Wubi, the NT Bootloader handles that task just as you described.

---

### Post by TheRevTastic on 2010-02-16
Well also, how would I go about uninstalling ubuntu when I installed it with the cd?

---

### Post by meierfra. on 2010-02-16
> If you install Ubuntu with Wubi, the NT Bootloader handles that task just as you described.

Please don't do that.   Since  Wubi lives inside a file on the Windows partition it gets corrupted much easier than a regular install. Just a couple of weeks ago, I worked on  case where the whole Wubi file system had disappeared just because the laptop run out of battery.
The only advantages of Wubi is that it can be installed easier. But you already installed Ubuntu. 

I don't really understand your original  question. Grub should also give you a boot menu where you can choose between Ubuntu and Windows.  Is there something wrong with the  Grub menu?

There are  ways to change the look of the Grub menu, if that's your problem

If you really want to, it is possible  to add Ubuntu to the Windows Boot loader. But I recommend against it.

---

### Post by TheRevTastic on 2010-02-16
Okay one more quick question.

I didn't use wubi to install Ubuntu 9.10. And when I try to get rid of it by deleting the partition, it makes it free space, won't let me add that space back to my Windows 7 Partition, and doesn't uninstall grub.

Anyway to fix that?

---

### Post by djchandler on 2010-02-17
> **TheRevTastic said:**
> Okay one more quick question.

I didn't use wubi to install Ubuntu 9.10. And when I try to get rid of it by deleting the partition, it makes it free space, won't let me add that space back to my Windows 7 Partition, and doesn't uninstall grub.

Anyway to fix that?

Remove any USB mounted storage device first.

Go back into Disk Management. If you right click on the main Windows partition and "extend volume" is grayed, then you didn't entirely remove the partition Ubuntu was on. This is also evident by not seeing any "free space" on the drive. Ubuntu usually creates an extended (not primary) partition and puts itself on "logical" partitions in the extended partition.

There are (at least) two partitions that Ubuntu is/was on. Windows disk management won't ID either one of them. Remove both logical disks *and* the extended partition. You should then see an area of the disk marked "free space." Right click on the the main Windows partition. The "extend volume" item should be black now. Select it and it will bring up a dialog to let you expand that partition. If there's only one hard disk, dis-regard the mesaages about spanning disks. 

Restart your computer.

Go into the BIOS and set the CD/DVD to be the first device to  boot, put the hard drive second. Put your Windows CD/DVD in the CD/DVD drive.

Boot from the CD/DVD,  enter the recovery console (press R when it asks you whether you want to  install windows etc.) When you get to the recovery console, type: 

[SIZE=3]**[FONT=Courier New]fixmbr [/FONT]**[/SIZE]

That will remove GRUB from your system.

---

### Post by Arand on 2010-02-17
Note, on post-XP CDs, there is no "fixmbr" command, instead use the commands:```
bootrec /fixmbr
bootrec /fixboot
```

If you want to use the windows bootloader to load ubuntu instead (actaully, to load grub, which in turn loads ubuntu) There is a guide available at [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux) which uses the windows boot config editor EasyBCD.

You can from the liveCD choose not to install the grub part to the mbr, but instead to the ubuntu partition, and then make the windows bootloader load grub from that partition.

Using the windows bootloader to load ubuntu will be more complex, simply because grub has tools to auto-detect windows, whereas the windows bootmgr does not have the ability to auto-detect ubuntu.
I'm not sure if you were looking for a simplicity, rather?

- Arand

---

