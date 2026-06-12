---
title: "How to uninstall ubuntu 11.04 or dual boot to run windows 7 alongside [help]"
date: 2011-11-23
forum: General Help
---

### Post by EBKS on 2011-11-23
I brought a computer from a guy and it has ubuntu 11.04 installed and the programs I need to run requires windows. I brought a windows 7 disc and it doesn't boot in ubuntu at all. Is there a way I can either remove ubuntu completely or run windows  alongside with ubuntu. -thanks

---

### Post by mikegior on 2011-11-23
Well, if you were looking to remove Ubuntu altogether, you can boot from the Windows DVD and do a standard installation, consisting of formatting the hard drive.

If you wanted Ubuntu after that you can download a program called Wubi and run it from within Windows. What Wubi allows you to do, is install Ubuntu within Windows in a dual-boot manner. You can allot as much disk space as you would like to the Ubuntu installation.

You can also download the latest Ubuntu ISO, burn it to a CD, and boot from it and install Ubuntu from the disk. During the installation, Ubuntu will ask if you would like to install it along side an operating system (which it will automatically detect) and you can also dedicate as much or as little space as you want to the Ubuntu installation.

---

### Post by raja.genupula on 2011-11-23
+1
1...You said its not booting , so try to look for errors in the cd.

2...One more thing is actually in ubuntu you have a application called WINE , you can use it run windows application on Ubuntu

3..Use virtual Box and install Windows in it . Run it when you need .

---

### Post by Mark Phelps on 2011-11-23
You mentioned boot "in Ubuntu".  If by that, you mean that you're starting the PC, and after Ubuntu is running, inserting the Win7 DVD -- that is NOT going to work.  You can't install Windows from inside Ubuntu.

Instead, boot from the DVD, and when the Win7 installer starts, use the option to erase the drive and use all of it.

If the PC does not boot from the DVD, then you will need to check your BIOS settings to confirm that the CD/DVD drive is listed before the hard drive.

If the Win7 installer does not provide the option to erase and use the whole drive, then you will need to erase the partitions on the drive, first.

You will need to boot from another CD in order to do that.  You can download and burn the free Partition Wizard ISO (for Windows), or you can download and burn an Ubuntu desktop CD (for Linux).

Then, you boot using the CD you burned and use that tool to remove all the partitions on the drive.

After that, you should be able to reboot using the Win7 DVD and do the installation.

If you encounter problems with that installation, or afterwards, strongly suggest you then visit the Windows 7 forums: sevenforums.com.

---

