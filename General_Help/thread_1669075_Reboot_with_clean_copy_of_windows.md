---
title: "Reboot with clean copy of windows"
date: 2011-01-17
forum: General Help
---

### Post by ledwardz on 2011-01-17
hey, i need to go back to windows but when i try to reboot from CD, it doesn't work. I don't want the two operating systems working side by side and so don't want to partition the disks soooo how do i do this?

Any help much appreciated, Thanks, lee.

---

### Post by cascade9 on 2011-01-17
Try going into your BIOS and setting the CD/DVD drive to boot 1st. 

Sometimes you can hit 'F8' during the boot process and get a set of options to boot from. Worth a try, but it doesnt work with every x86 computer.

---

### Post by MARP1961 on 2011-01-17
If you have already installed Ubuntu on a partition of your hard drive and you are dual-booting with Windows, you will need to do a repair or even reinstall of Windows if you simply delete Ubuntu.

Ubuntu overwrites the Windows bootloader with it's own (Grub). If you delete the Ubuntu partitions, the Grub bootloader will be deactivated and Windows will become unbootable. The simplest thing to do is just leave Ubuntu and Windows as they are! If you want Ubuntu completely gone, then you will need a bootable Windows install or repair CD that can fix the 'damaged' Windows Master Boot Record (MBR). If for some reason you cannot fix MBR, you will need to perform a reinstall of Windows. Do you have the right version on a CD to do this? Remember the Windows Product Code will need reentering and validating. If you have an OEM Windows sticker you may not have a disk. It might be possible to burn one yourself if you have a recovery partition. I know you can with Vista, not sure about XP.

---

### Post by ajgreeny on 2011-01-17
I don't understand what you are asking.

Do you already have a windows install, or are you wanting to get rid of Ubuntu and go fully back to windows with no Ubuntu on the computer?

If you don't want to partition the disk, and if you want windows alone you will have to format the partitions on the disk as you can not have the different OSs on the same file-system.

If you want to keep Ubuntu and also have windows but not as a separate partitioning exercise, your only option is a windows virtual machine in something like VirtualBox.

Tell us more of what you mean in your original post, please.

---

