---
title: "error: no such partition"
date: 2011-01-25
forum: General Help
---

### Post by jammedubu on 2011-01-25
Hello,

I deinstalled Ubuntu today. Just deleted the partitions etc and thought it would be fine, but now this weird grub thing is telling me:
error: no such partition
grub rescue>

I am at the end of my wits:
I downloaded a liveCD, which will not boot. My XP cd boots but gets a blue screen afterwards
I downloaded a windows 7 live cd which did not help either
I hit my computer, didn't help.

Problem is, I can't load my bios anymore to change the boot order...
Didn't even know Grub was part of linux...

Point is, I got a presentation tomorrow and all my important files are on that laptop. . . 
please help
and o yea, the setroot=(hd0,0) gives no response. I tried a bunch of other commands but I keep getting unknown command...

---

### Post by Bucky Ball on 2011-01-25
Were you dual-booting with Windows? Thing is, grub writes itself to the MBR and that is what you're booting from. Nothing for it to find obviously. Do you have a Windows install in there? What is there? What do you want to be there?

No offence but a pretty radical move; with no back-up of your important files, assumed it would work fine, and you have a presentation tomorrow! Where exactly were the important files?

As for none of your CDs booting, that might be a separate issue, along with not being able to get into the BIOS to change your boot selection. If you *can* get a LiveCD to boot, then 'Try Ubuntu', get to a desktop, and transfer your important files to a USB or external hard drive, but I guess that is what you are trying to do. ;)

---

### Post by jammedubu on 2011-01-25
I know, it's all but smart...
Yes I was dual booting with windows 7. 
I am curious... the file structure of a windows vista boot disk is different as that of a windows 7. . . Might that work on a system with windows 7 on it ?

---

### Post by Bucky Ball on 2011-01-25
Well, you need to reinstall the Windows boot to the MBR. There is a simple process but as I haven't tweaked with Windows in a long while I have no memory of what that is. Sorry. You might be able to find instructions.

Just had a quick look and I think 'chkdsk' is what you want. It will fix and repair errors on the disk, including, from memory, the MBR. Someone more knowledgable on this can hopefully chime in. 

And, hey, we all make mistakes! ;) Otherwise how would we learn anything!!

---

### Post by efflandt on 2011-01-25
If you can get an Ubuntu install CD to boot to a live system (which might require pressing a certain key during BIOS splash screen), this explains how to fix the mbr from there [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

You should check with gparted if the correct partition is marked as the boot partition.  However, that might not be the partition you think it is.  For example current Dell computers typically boot from their RECOVERY partition instead of the partition with Win7.  If in doubt, run the [boot info script]("http://bootinfoscript.sourceforge.net/") and see which partition contains:

```
Boot files/dirs:   /bootmgr /Boot/BCD
```But are you trying to get into Win7/Vista or WinXP (either would use the same mbr, but boot files might differ).

---

### Post by Bucky Ball on 2011-01-25
> **efflandt said:**
> If you can get an Ubuntu install CD to boot to a live system (which might require pressing a certain key during BIOS splash screen), this explains how to fix the mbr from there [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

You should check with gparted if the correct partition is marked as the boot partition.  However, that might not be the partition you think it is.  For example current Dell computers typically boot from their RECOVERY partition instead of the partition with Win7.  If in doubt, run the [boot info script]("http://bootinfoscript.sourceforge.net/") and see which partition contains:

```
Boot files/dirs:   /bootmgr /Boot/BCD
```

Don't think OP wants Ubuntu on HDD (and hasn't got it by the sounds as all EXT partitions have been removed which is why grub is complaining), just wants to boot back into Windows. Will your method repair the Windows boot loader/record and kill the grub that is written to the MBR? I am assuming that is what's required. ;)

---

### Post by jammedubu on 2011-01-25
I solved it myself with an ace solution I found here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

The only catch is that the only livecd working, is the Vista one. As I thought, it's the filestructure that made the vista cd bootable.

Thanks everyone adding their 2 cents.

---

### Post by Bucky Ball on 2011-01-25
[http://www.tomstricks.com/how-to-repair-and-restore-windows-vista-master-boot-record-mbr/](http://www.tomstricks.com/how-to-repair-and-restore-windows-vista-master-boot-record-mbr/)

---

