---
title: "Booting problem"
date: 2010-12-26
forum: General Help
---

### Post by jkfsjaklfa on 2010-12-26
I've got a problem with my new laptop computer... I was forced to buy a computer with Windows, so I decided to keep it on the computer in case I would need it for something at some point, although I told the Ubuntu installer to make the Windows partition as small as possible. So my computer has Windows 7 and Ubuntu 10.10. The Ubuntu installer set up a boot loader so that I could select if I wanted to use Ubuntu or Windows. I started Ubuntu and started doing things with the computer and installing a few programs. Then I decided to start Windows, and Windows wanted to install some updates and after that it wanted the computer to reboot, so I did that.

Now the computer won't boot. It seems that something (Windows?) has changed the partition I'm booting the computer from. I'd like to boot my computer from the partition containing the boot loader so that I can select which OS to use, or, failing that, at least boot from a partition containing an OS (and preferably Ubuntu). How do I do this? The only way to boot my computer for the moment seems to be to boot from the Ubuntu installation disc, using the "try Ubuntu" option".

Using the "try Ubuntu" option, I go to the menu bar and select "System: Administration: Disk Utility" to view my partitions. I see six of them:

DELLUTILITY (105 MB FAT)
Recovery (16 GB NTFS)
OS (22 GB NTFS)
Exteded (282 GB, containing the following two partitions)
Unnamed partition (272 GB ext4)
9.4 GB Swap Space (9.4 GB)

Which of the partitions contains the boot loader and how do I tell the computer that I want to boot from that partition? Considering the file system types, I would assume that it is one of the latter ones. In the Ubuntu installation program, I used "Install alongside other operating systems":
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_03_medium.jpg[/IMG]
And then I decreased the Windows partition to the smallest possible size:
[IMG]http://www.ubuntu.com/sites/default/files/active/maverick/install_04_medium.jpg[/IMG]
I'd like to fix my computer, but I'm not sure how to do it.

I don't know if it matters, but the only partition listed as "bootable" is the one called "recovery".

---

### Post by oldfred on 2010-12-26
You probably just need to reinstall grub2. But the real problem is Dell Utilities that write into the MBR area and corrupt grub2. Grub is working on workarounds for some of those apps, but most users are not really using them or can use something else and just uninstall the offending apps.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
[http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable](http://linux.slashdot.org/story/10/08/28/2112208/Some-Windows-Apps-Make-GRUB-2-Unbootable)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, flexnet and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Bootable only means something to windows as it uses the boot flag to know what partition to boot.

---

### Post by jkfsjaklfa on 2010-12-26
Thanks, I got the boot menu back again. I'll look into disabling the problematic software tomorrow.

---

