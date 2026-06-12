---
title: "dualboot issues"
date: 2011-07-13
forum: General Help
---

### Post by WestCoastSunset on 2011-07-13
OK, 2 problems which are kind of related.  I have an older asus motherboard (p4p800) with a pentium 2.26 ghz non threadable processor (got it from an old pc).  

My first problem is with the live cd. When I get to the desktop the screen flickers and turns black so much it is impossible to do anything.  When I boot into ubuntu I always have to turn off all effects.  Any way of doing this with the live cd so I can fix grub?

My second issue is dualbooting windows XP and ubuntu.  Both are on the same drive and ubuntu is installed to /dev/sda5 and I believe xp is on /dev/sda1.  There is also the swap.  No boot partition.

I just want to boot ubuntu from the windows bootloader.  I'm assuming the dd command is part of this but how do I install grub to /dev/sda5?

I thought the command would be something like grub-install /dev/sda5.  Then I would create the image file with the dd command to put on the c: drive in windows.  

I believe the grub vercion is 1.99 rc1 (not sure why a release client is on a stable version of linux, but I may have grabbed the wrong cd file)

Am I missing something? 

Should I create a boot partition?

FYI:  I already know how to recover the Windows xp MBR.

Thanks for any help you can give.

---

### Post by varunendra on 2011-07-14
For the flicker issue, try this:

[LIST=1]
[*]Press and hold 'shift' key while booting from the CD. This will bring up advance boot menu.
[*]Press F6, then in the popped up menu, check (by pressing 'spacebar') 'nomodeset'.
[*]You may also disable other items in the same menu if you face other problems during boot-up.
[*]Select 'Test without installing' and press Enter (trivial I know :) )
[/LIST]
I believe it is not possible for XP boot loader (ntldr) to boot ubuntu, unless you use a third party software to accomplish that. But if you have installed Ubuntu on a separate partition, Grub should have already taken care of dual boot issue. That is, you should have been presented with Grub menu, asking to select the desired OS to boot.

Did you install XP AFTER Ubuntu? If so, you can follow this guide to restore grub on the MBR: [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

If this is not what you want or doesn't solve your problem, please mention the version of ubuntu you are using. Also, it will be much better if you could post results of [boot info script]("http://bootinfoscript.sourceforge.net/").

---

### Post by Bucky Ball on 2011-07-14
There is a great tool for restoring grub to the MBR very easily from within Ubuntu:

[http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html](http://www.webupd8.org/2011/06/boot-repair-fix-ubuntu-boot-issues.html)

Takes seconds and you will have the option of either OS at next reboot. ;)

---

### Post by WestCoastSunset on 2011-07-15
Thanks, The nomodeset option worked.  Still looking to see if I can boot ubuntu from windows xp bootloader but I don't think it is possible.

---

### Post by Mark Phelps on 2011-07-15
> **WestCoastSunset said:**
> Thanks, The nomodeset option worked.  Still looking to see if I can boot ubuntu from windows xp bootloader but I don't think it is possible.

NO -- it's not.

NeoSmart Technologies makes a product known as EasyBCD, which DOES allow you to boot into Linux distros from Windows, but it only works with Vista or Win7, it does not work with XP.

---

### Post by Bucky Ball on 2011-07-15
> **WestCoastSunset said:**
> Still looking to see if I can boot ubuntu from windows xp bootloader but I don't think it is possible.

Not sure why. I'd just go with Grub, personally. (Lilo is also another option.)

If you go with Grub, boot into Ubuntu, open a terminal (Applications>Accessories>Terminal) and paste this in:

```
sudo update-grub
```

Reboot and you will have the option of either OS. That easy.

---

