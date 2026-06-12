---
title: "New triple-booted Ubuntu installation doesn't load grub2"
date: 2011-08-05
forum: General Help
---

### Post by h2g2guy on 2011-08-05
I'll start with the tl;dr version, then get to the full story later on.  System specifications are at the end of the post, along with a link to a forum post on a separate site that may be relevant.  

I'm attempting to triple boot Windows 7, Mac OS X, and Ubuntu 11.04 on non-Mac hardware.  Chameleon is my primary bootloader, which is supposed to chainboot into grub2, but all I get when I choose the Linux boot option is a black screen with blinking cursor.  If I try to boot Ubuntu while holding shift, I get the word GRUB, followed by a space and a blinking cursor.  grub2 is installed to the Ubuntu partition, and attempts to reinstall it there or to the MBR from a LiveCD result in errors.  The MBR and GPT partition tables are synchronized.  How do I go about making Ubuntu bootable, without breaking my other two operating systems (or at least leaving them recoverable)?

Full story follows:

About a week ago, I built a new desktop computer.  The goal was to triple boot the system with Windows 7, Mac OS X Snow Leopard, and Ubuntu 11.04.  This endeavor has been significantly more complicated than I originally expected, but with the help of a forum-goer at InsanelyMac.com, I've managed to get pretty far with a complex installation process.  I've attempted to get Ubuntu running using two methods, neither of them achieving what I'm hoping.  Both methods follow.  

In the first method, I install Mac OS X using a specially designed install CD that boots into the Snow Leopard installation DVD.  The disk is partitioned to have a FAT partition, followed by a Mac OS X journaled partition, ending in a second FAT partition.  Mac OS is then installed to the second partition.  The Windows boot CD is then used to format the first FAT partition as NTFS, which Windows 7 is then installed to.  As I'm sure you know, this installs Windows Boot Manager.  Then I boot into OS X using the boot CD mentioned earlier, and install Chameleon, a bootloader specifically designed for Hackintosh systems, and (supposedly) capable of booting into all three operating systems I'm trying to work with.  Finally, I divide and reformat the remaining FAT partition into an ext4 partition and a swap partition, and install Ubuntu to that ext4 partition, with the bootloader installed to the same partition.  This will break the Windows bootloader, as now the MBR and GPT tables are no longer syncronized.  Ubuntu is also unbootable; attempting to chainload into grub2 leaves me at a black screen with a blinking cursor.  The former problem is solved by booting into a LiveCD and installing and running gptsync.  Windows is now bootable, but Ubuntu remains in 'limbo'.  

The second method I attempted is very similar, but deviates in the last few steps.  After installing Windows, I instead install Ubuntu 10.04 LTS, as I thought I might have fewer bootloader issues with that distribution (don't ask why; it was a lucky hunch).  This breaks Windows Boot Manager, but this time grub2 throws me into the grub> prompt.  I can boot into Ubuntu just fine using the set root/linux/initrd/boot commands, but my motherboard's Ethernet port is not detected by the OS, so I can't directly download and run gptsync.  Once I do manage to run it, though, Windows is then also repaired.  Unfortunately, since I can't access the Internet, I can't do a distribution upgrade that way.  Trying to upgrade from the recent release's LiveCD...well...doesn't upgrade, just overwrites.  So I get the same black screen with blinking cursor problem.  

I've tried reinstalling grub2 through a LiveCD using grub-install both using the --root-directory flag and the chroot method.  

I'm at my wit's end.  What am I missing?  

System specifications:  
Intel Core i7 (LGA1155)
Corsair VENGEANCE 4x4GB DDR3
Two EVGA nVidia GeForce GTX 460 2048MB 
3TB Hitachi hard drive
LG SuperMulti optical drive
ASUS P8P67 PRO motherboard
Thermaltake 1050W PSU

This forum post was what I used to get my OS X installation up and running.  I don't know if it would be of any use to you guys, but I'll give it to you anyway:  [http://www.insanelymac.com/forum/index.php?showtopic=263940](http://www.insanelymac.com/forum/index.php?showtopic=263940)

Thanks so much!

---

### Post by dcstar on 2011-08-06
> **h2g2guy said:**
> 
..........
The second method I attempted is very similar, but deviates in the last few steps.  After installing Windows, I instead install Ubuntu 10.04 LTS, as I thought I might have fewer bootloader issues with that distribution (don't ask why; it was a lucky hunch).  This breaks Windows Boot Manager, but this time grub2 throws me into the grub> prompt.  **I can boot into Ubuntu just fine using the set root/linux/initrd/boot commands**
.........

Boot the installed Ubuntu and then do this to have Grub installed on whatever boot drive you are using and detecting all available OSs:

```
sudo dpkg-reconfigure grub-pc
```

---

### Post by h2g2guy on 2011-08-07
Unfortunately, I tried to reinstall 10.04 in order to do that, but the grub> prompt didn't appear this time.  I got exactly the same symptoms that I get with 11.04.

Tried reinstalling one more time with the same results, so I used a LiveCD to mount /dev/sda4 to /mnt, then mounted /dev, /proc, and /sys to the appropriate locations in /mnt.  I then chrooted into /mnt and ran dpkg-reconfigure from there, hoping that that would do something helpful.  It completed with apparent success, but there was no change in the behaviour of the system.  

Thanks for the idea, though!  Any other possibilities?

---

### Post by overdrank on 2011-08-07
Doesn't Apple's EULA limit the installation of OSX to Apple hardware?
Thread closed.

---

