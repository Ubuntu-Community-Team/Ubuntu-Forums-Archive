---
title: "Restoring Netbook to factory settings problem"
date: 2009-11-12
forum: General Help
---

### Post by cozski on 2009-11-12
Hello

I have an Acer Aspire One  ZG8 running WinXP. I installed Ubuntu 9.10 using flash drive installation with no problems, so had a dual boot option. I then came across the Netbook Remix and thought that maight be a more appropriate version to install. I read the installation notes which I think informed me that I could install it over the previous version of Ubuntu... it would just simply wipe it from my drive. After several attempts I believed I had successfully installed but at the Grub Loader I was being given 3 boot choices: WinXP and 2 Ubuntu (there was nothing to distinguish the Ubuntu versions... they just looked like the original version that I had installed). When I selected to run one of the versions of Ubuntu I couldn't get past the Password prompt... incorrect password. When I restarted from that point it would never return to the Grub loader... just come straight back to user/password prompt.

So I decided I would restore the Netbook to factory settings and re-install Netbook Remix. Using the Acer Aspire Recovery Management Program I simply selected the option to Restore to Factory settings. It started to reboot but now it never gets beyond a black screen with "Grub loading stage 1.5 / GRUB loading. Please wait... Error 17" I think I did something wrong :( I can CTR+ALT+DEL to restat the boot process and I can access my BIOS but beyond that... nothing else.

Any advice and help greatly appreciated. I still have my bog standard laptop running with Ubuntu and XP but i'd love to get my Netbook back up and running.

Thanks

Coz

---

### Post by Giblet5 on 2009-11-12
I assume that you are booting from CD...

Open a terminal window and execute: ```
sudo fdisk -l
```

Post the output in a CODE block (click the '#' icon at the top of the comment editor).

This will display the partitioning of your hard disk drive, and we can use that to fix this.


Edit: Curious as to why people post questions, then abandon the thread... Why bother asking?

---

### Post by cozski on 2009-11-12
Thanks... I'll do as you suggested. I'm not sure what you mean by abandoning the thread in relation the question I asked... I was in work when I posted and couldn't return to it until now. Apologies if that was unacceptable behaviour.

I'm not booting from  CD... I'll have to boot from flash drive I think... but I;ll post the info as soon as I get it.

Regards

---

### Post by cozski on 2009-11-16
```
           ubuntu@ubuntu:~$ sudo fdisk -l  
 omitting empty partition (5)  
 

 Disk /dev/sda: 160.0 GB, 160041885696 bytes  
 255 heads, 63 sectors/track, 19457 cylinders  
 Units = cylinders of 16065 * 512 = 8225280 bytes  
 Disk identifier: 0xd1a40721  
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sda1   *           1        1045     8388608   12  Compaq diagnostics  
 /dev/sda2            1045       18806   142668766    7  HPFS/NTFS  
 /dev/sda3           18807       19457     5229157+   5  Extended  
 /dev/sda5           18807       19110     2441817   83  Linux  
 /dev/sda6           19111       19132      176683+  82  Linux swap / Solaris  
 /dev/sda7           19133       19435     2433816   83  Linux  
 /dev/sda8           19436       19457      176683+  82  Linux swap / Solaris  
 

 Disk /dev/sdb: 8019 MB, 8019509248 bytes  
 247 heads, 62 sectors/track, 1022 cylinders  
 Units = cylinders of 15314 * 512 = 7840768 bytes  
 Disk identifier: 0xb0bcd68e  
 

 This doesn't look like a partition table  
 Probably you selected the wrong device. 
 

    Device Boot      Start         End      Blocks   Id  System  
 /dev/sdb1   ?      210485      226594   123339962   78  Unknown  
 Partition 1 has different physical/logical beginnings (non-Linux?):  
      phys=(518, 102, 15) logical=(210484, 238, 50)  
 Partition 1 has different physical/logical endings:  
      phys=(743, 0, 62) logical=(226593, 24, 15)  
 Partition 1 does not end on cylinder boundary.  
 /dev/sdb2   ?       28267       78919   387841909+  10  OPUS  
 Partition 2 has different physical/logical beginnings (non-Linux?):  
      phys=(205, 7, 0) logical=(28266, 90, 14)  
 Partition 2 has different physical/logical endings:  
      phys=(920, 235, 50) logical=(78918, 75, 34)  
 Partition 2 does not end on cylinder boundary.  
 /dev/sdb3   ?      122082      247408   959615034   8b  Unknown  
 Partition 3 has different physical/logical beginnings (non-Linux?):  
      phys=(260, 125, 54) logical=(122081, 227, 56)  
 Partition 3 has different physical/logical endings:  
      phys=(893, 46, 60) logical=(247407, 29, 35)  
 Partition 3 does not end on cylinder boundary.  
 /dev/sdb4   ?       86686       87229     4161547    a  OS/2 Boot Manager  
 Partition 4 has different physical/logical beginnings (non-Linux?):  
      phys=(269, 111, 50) logical=(86685, 50, 27)  
 Partition 4 has different physical/logical endings:  
      phys=(0, 0, 0) logical=(87228, 172, 54)  
 Partition 4 does not end on cylinder boundary.  
 

 Partition table entries are not in disk order  
 ubuntu@ubuntu:~$  
 
```I hope this is what you meant. I'm afraid I had terrible trouble trying to reboot using the usb drive... but eventually managed it... I think. Above is the info.

Thanks

Coz

---

### Post by coffeecat on 2009-11-16
First - ignore Giblet5's edit comment. I think it's very rude. Assuming a thread has been abandoned after only 40 minutes is absurd.

Anyway, to your problem. :) It's difficult to tell what the Compaq diagnostics utility did because it has not deleted the Linux partitions (according to your fdisk output), but the error 17 suggests that something has gone wrong with them. That would accord with the grub loading 1.5 message - it's looking for grub stage 2 which is in the Ubuntu root partition (one of them). Grub stage 2 has the grub menu, and if it can't find it - no menu - no bootup.

I can't quite follow your first post. Do you mean that every time you try to boot up, you get the "Grub loading stage 1.5 / GRUB loading. Please wait... Error 17", or did you only get that once and now you can't get past the BIOS?

Anyway - a few thoughts. You can download [Super Grub Disk]("http://www.supergrubdisk.org/"). Follow the links on the right for the USB version and how to get it onto a USB stick. There's instructions for both Linux and Windows. When you boot up with SGD, there's two options for Windows - simply boot into Windows, or repair the Windows MBR (presently overwritten by grub stage 1) and then boot into Windows. That, at least will give you Windows back. Then you can think about what you want to do with the broken Ubuntu partitions. I would imagine the best option would be to boot up with the USB live installer and run Gparted from that to delete all the Ubuntu partitions and then to start over.

I'm sorry if this is not completely clear. It's late here and I'm logging off soon so you won't get another post from me within 40 minutes. :wink: But I'll drop by tomorrow and pick this up when I can. And I've subscribed to this thread so I won't miss it if you can't post back for a couple of days. I'm more patient than certain forum members I could mention. :p

---

### Post by cozski on 2009-11-16
Thanks for the response and advice. Much appreciated.

In response to your question and in the hope that I may be clearer about the situation. When I decided to restore my netbook to factory settings, I used the Disk Recovery Management Utility in Windows... it prompted me with the usual cautionary warnings about losing data  but I chose to proceed anyway as this was what I wanted. Anyway, it immediately said it needed to re-boot and attmepted to... it was at this point that it started to reboot and I got the "error 17" message. I can access BIOS just before I get the message if I select F2. I can also access my boot sequence through BIOS so in response to the previous advice in my original post, I used my USB with a Live Ubuntu version on it to access my netbook. This then enabled me to post the info above.

I was pretty certain that my XP OS was untouched because it simply went to re-boot far too quickly for me to think anything of any significance had happened. I can still see the partitions when I use the GParted utility. I will do as you have suggested using the Super Grub Disk and return to it when I've done it. It will also be tomorrow as it's late here and I too will be logging off. Thanks again.

---

### Post by coffeecat on 2009-11-17
Hi there.

A few further thoughts. I suggested using SGD to repair the Windows MBR simply to give you the reassurance (hopefully) of being able to boot into Windows. The moment you install Ubuntu again, the Windows mbr will again be overwritten with grub stage 1, but that won't matter so long as you have an unbroken Ubuntu partition with grub stage 2 in it.

A more direct way of getting you up and on the road again would be to boot up with the live Ubuntu USB desktop, go into System > Adminstration > Gparted and delete the two swap partitions and the two ext3/4 partitions. You have to highlight each swap partition in turn and choose Partition > swapoff before you can delete them by the way. Once you've deleted the (logical) Linux partitions, delete the extended partition (sda3).

But before you start the installer, there's one more step to take. I was too tired to calculate the space devoted to your Linux partitions last evening, but I've done this this morning, and there's a problem. Your partition sizes are (approximately):

sda1 - Compaq - 8GB
sda2 - Windows - 136GB
sda3 - Extended ~ 5GB
which contains:
sda5 - one of the Ubuntu root partitions - 2.3GB
sda6 - one of the swaps - 0.16GB
sda7 - the other Ubuntu root partition - 2.3GB
sda8 - the other swap - 0.16GB

Those Linux partitions are hopelessly small. I'm surprised Ubuntu ran at all. A default installation of Ubuntu takes up about 2.3GB even before you add personal data and extra apps. Even 5GB is a bit on the lean side, so I suggest (if you follow this route) that once you've deleted the Linux partitions, you shrink the Windows partition a bit more - say by at least 3GB leaving you 8GB in total for Ubuntu. Even that's lean if you want to install several apps and keep much personal data. Then you can start the installer and, at the partitioning stage, choose the 'use the largest continuous free space' option.

Anyway - the choice is yours. Use SGD to get Windows (alone) up and running to give you breathing space and thinking time, or go straight for the reinstall, which will give you a Windows boot option in the newly-installed grub menu.

---

### Post by cozski on 2009-11-28
Okay, first things first... apologies for the delay... had to hightail it to England unexpectedly for a funeral and PC related issues took a back seat.

I attempted to use the Super Grub Disk (usb version) and followed the instructions to the letter, but could not get it to work. I repeatedly got a Error 22 message when trying to associate the usb. I'm not familiar with command lines in the Terminal function... so I scrolled further down and noticed the Windows option (UNetbootin) which was remarkably simple. I then used the SGD via usb... it allowed me to boot into the Windows operating system. I could also see the previous Ubuntu systems that I'd put on. It immediately resumed the Factory Settings Restore process that I had initiated so I continued with that. It is now going through that process and I'm waiting for it to complete. Hopefully that will then allow me to at least return back to having dual boot options at the very least. Obviously I still have 2 Ubuntu on the system but I'll hopefully resolve that when this process is complete...

Thanks again for the invaluable suggestions & advice... much appreciated. And this hasn't put me off using Ubuntu in the slightest :D

---

