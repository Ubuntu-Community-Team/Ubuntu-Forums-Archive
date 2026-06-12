---
title: "Multiple OS help"
date: 2012-01-26
forum: General Help
---

### Post by baqar on 2012-01-26
I installed Windows XP first [as i need it]
Then i installed Win 7
and then install Ubuntu 11.10

but now at boot, i only see the menu for Windows 7 and for Ubuntu...
any help to load Windows XP
as i need XP first 
Thank in advance everyone

---

### Post by hhh on 2012-01-26
> **baqar said:**
> but now at boot, i only see the menu for Windows 7 and for Ubuntu...

I've never triple booted with two versions of Windows, but have you booted into the Windows partition yet? I'm wondering if when you choose the Windows option you are prompted with another screen that lets you choose between 7, XP and Windows Recovery (for example).

---

### Post by oldfred on 2012-01-26
Your issue is with Windows. Windows only boots from the active partition or the one with the boot flag. Additional installs of Windows literally move all the boot files to the active partition. So only one Windows is really the bootable partition and since there are no boot files in other Windows installs, grub will not boot them.

You many be able to move boot flag, move the boot files, and run Windows repairs to fix the second install, if it is in a primary partition.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

### Post by Double.J on 2012-01-26
Hi there, I think Oldfred's given you all the info you really need :)

My vote is for [easyBCD]("http://neosmart.net/EasyBCD/") - If you have win7 involved with multi OS, and you're not just dual booting Ubuntu, I always find it the easiest to maintain - too many distro's and BSD's not auto-detected by grub. If you use easy BCD, and add another distro, just tell it to install it's bootloader to it's own partition and make an entry for it in easy :)

For now, I suspect hhh is correct, and win7's loader already created an entry for XP

All the best!

---

### Post by C.S.Cameron on 2012-01-26
I recently purchased a HP mobile work station, (laptop).
HP fills up all four partitions so first I deleted the Tools partition.

Then I used the method on this page to install XP, (I needed to use a version of XP that came with SATA drivers):

[http://www.howtogeek.com/howto/8790/dual-boot-your-pre-installed-windows-7-computer-with-xp/](http://www.howtogeek.com/howto/8790/dual-boot-your-pre-installed-windows-7-computer-with-xp/)

This worked great for a W7 x XP dual boot.

I have not yet tried installing Ubuntu for a triple boot yet as I am not sure which HP partition to remove next.

---

