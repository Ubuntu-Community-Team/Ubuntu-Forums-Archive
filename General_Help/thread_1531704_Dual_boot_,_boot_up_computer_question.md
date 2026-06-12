---
title: "Dual boot , boot up computer question"
date: 2010-07-15
forum: General Help
---

### Post by apvm on 2010-07-15
I have 2 hard drives.....C: windows 7 installed and I could not get more than 5GB from it
 
D: I could make a new 20Gb partition from it and installed Ubuntu on it.
 
 
My question is once Computer boot up, it shows a screen that I could choose a few Ubuntu and safe mode etc with Windows 7 loader being the last option.
 
If I pick the 1st Ubuntu...there is no problem booting up Ubuntu but if I pick Windows 7 loader, it show me another page with either Ubuntu or Windows 7, ie I have to pick twice before I could boot Windows 7
 
So is there a way I could just have a page to either pick Windows 7 or Ubuntu?
 
Also when I install Ubuntu 10.04 onto the 20GB I forgot to make a swap space, does it matter? If it does, can I use the 20GB as swap space?
 
Tia

---

### Post by aidin36 on 2010-07-15
For swap, take a look at this:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by oldfred on 2010-07-15
Did you or do you also have wubi installed? That should be the only way you get a Ubuntu entry in the windows boot files. 

I think with win7 it is BCDedit to edit the boot options.

---

### Post by apvm on 2010-07-15
I burnt the Ubuntu iso onto a DVD since I have no CD, it couldn't boot up so when I open the DVD in Windows it said to install something to help boot from CD, so can I unstall that and just use Windows 7 loader since it has only two option Windows 7 or Ubuntu.

---

### Post by WorMzy on 2010-07-15
I burn all my isos to DVDs since I have no CDs, and they all work fine. Of course I always use Linux to burn isos to disks though, so I couldn't say whether you need to set a "bootable" option or something in a Windows-based iso burner.

It sounds to me, from the first post, that you have two installations of Ubuntu: one installed to a partition, and one installed inside Windows as a Wubi installation. If you have installed Ubuntu to it's own partition, you can uninstall Wubi by using Add/Remove Programs inside Windows., removing Wubi should remove the boot option from the Windows bootloader.

But from your second post, it sounds like you *haven't* installed Ubuntu to it's own partition, which confuses me, because AFAIK, you shouldn't see the Grub bootloader, and if you do, it certainly shouldn't be before the Windows bootloader.

---

### Post by apvm on 2010-07-15
> **aidin36 said:**
> For swap, take a look at this:
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
 
 
Very complicated for a newbie, I have 20GB with 4MB ram....how much swap file would you suggest?  tia

---

### Post by apvm on 2010-07-15
> **WorMzy said:**
> I burn all my isos to DVDs since I have no CDs, and they all work fine. Of course I always use Linux to burn isos to disks though, so I couldn't say whether you need to set a "bootable" option or something in a Windows-based iso burner.
 
It sounds to me, from the first post, that you have two installations of Ubuntu: one installed to a partition, and one installed inside Windows as a Wubi installation. If you have installed Ubuntu to it's own partition, you can uninstall Wubi by using Add/Remove Programs inside Windows., removing Wubi should remove the boot option from the Windows bootloader.
 
But from your second post, it sounds like you *haven't* installed Ubuntu to it's own partition, which confuses me, because AFAIK, you shouldn't see the Grub bootloader, and if you do, it certainly shouldn't be before the Windows bootloader.
 
 
The loader that come 1st after I turned on computer and bios post...is an option to boot into 4 Ubuntu...2 with Safe mode and the 5th is Windows 7 loader.
 
I have no Wubi installed but there is Ubantu installed according to Windows add/remove program, so I unintalled it.
 
BTW, I double checked the 20GB partition with Windows 7 Disk Management, that partition was unallocited before and now is Healthy Primary partition.....ie now I have two Healthy Primary partition on the same drive...so I suppose Ubuntu is installed in that 20GB partition.
 
I'll check what will happen when I have time to reboot. Thanks

---

### Post by apvm on 2010-07-16
All solved, thanks to all the replies.
 
Made a 1024.wsap for swap file and it works
 
uninstalled ubuntu from windows and now dual boot works fine.

---

