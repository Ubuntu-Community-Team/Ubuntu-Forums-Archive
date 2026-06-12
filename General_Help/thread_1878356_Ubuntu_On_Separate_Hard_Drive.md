---
title: "Ubuntu On Separate Hard Drive"
date: 2011-11-09
forum: General Help
---

### Post by Bosnic on 2011-11-09
So here's my dilemma:

I have 2 hard drives. One had Windows installed, and the other Ubuntu. When I set the Windows hard drive as my default (bios), I get an unwanted GRUB menu. I didn't want the Ubuntu installation to affect the boot when I chose my Windows hard drive, but it seems it has. After this, I went into Ubuntu and changed the GRUB settings so that the timeout was 0, and Windows was my default. This would make it seem like the Windows boot was unaltered.

Unfortunately, now I realized that I can't boot my Ubuntu hard drive simply by choosing to boot from it in my BIOS. It's completely dependent on the GRUB menu that comes up when I boot into my Windows hard drive.

Questions:

1. How do I access Ubuntu again?
2. How can I make it so my Windows hard drive is unaffected by my Ubuntu installation? Is GRUB installed on my Windows hard drive?

---

### Post by Bosnic on 2011-11-09
Anyone?

---

### Post by oldfred on 2011-11-09
Timeout to 0 is always a problem. Does holding shift key down from BIOS until menu give a menu? Otherwise you may have to boot from liveCD and manually edit grub.cfg (the file you really are not supposed to edit). I also have had grub recognize key press before menu even appears. You could try down arrow while BIOS ends to see if it catches it before booting Windows.

You need to reinstall grub to sdb and reinstall a Windows boot loader to sda. Then grub will let you boot either system and you can set default to Windows if you want, just not zero timeout. And in BIOS you could directly boot Windows.

Once you get into Ubuntu, your second drive is probably sdb, but check with fdisk before hand. This will reinstall to the drive you chose and then updates will also go to that drive.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

From Ubuntu you can install lilo's boot loader to sda, which works just like the Windows boot loader in the MBR.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

I do not think these are your issue but may help.
Discussion of timeouts issue & recordfail:
[http://ubuntuforums.org/showthread.php?t=1717700](http://ubuntuforums.org/showthread.php?t=1717700)
drs305's hack to get hidden timeout to work:
[http://ubuntuforums.org/showthread.php?t=1319672](http://ubuntuforums.org/showthread.php?t=1319672)

You may be able to boot with supergrub and bypass the timeout?
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Bosnic on 2011-11-09
I was able to install GRUB on the Ubuntu drive. However, I don't have a Windows CD to replace GRUB on the Windows drive. What should I do?

At best, I want to make it so my Windows drive uses its regular boot MBR. However, I'll settle for somehow hiding the GRUB menu on the Windows drive.

What are my options?

---

### Post by oldfred on 2011-11-09
Lilo as posted above works just like the Windows boot loader. Window boot loader really just checks for the active partition (boot flag) and jumps to it to continue booting. When grub chainloads to the Windows partition it is just jumping to the same location.

Lilo's only difference is it will jump to a logical partition where Windows will not.

Otherwise you need a Windows disk and run fixMBR to repair the MBR.

---

### Post by fantab on 2011-11-09
> **Bosnic said:**
> I was able to install GRUB on the Ubuntu drive. However, I don't have a Windows CD to replace GRUB on the Windows drive. What should I do?

At best, I want to make it so my Windows drive uses its regular boot MBR. However, I'll settle for somehow hiding the GRUB menu on the Windows drive.

What are my options?

What kind of a computer do you have? Laptop or Desktop? Is it branded and did it come with pre-installed Windows?

If it did come with pre-installed Windows then the chances are there will be a windows RECOVERY PARTITION. You can use this to Repair Windows.

Or you can REINSTALL WINDOWS if you insist on having "pure" windows.

---

### Post by Bosnic on 2011-11-10
Fixed.

I used Boot Repair in Ubuntu. It had the option to restore my original Windows boot MBR. Worked perfectly.

Thank you all.

---

