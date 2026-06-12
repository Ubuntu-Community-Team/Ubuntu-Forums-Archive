---
title: "Grub Recover??"
date: 2010-07-22
forum: General Help
---

### Post by MetaX on 2010-07-22
I have windows 7 on my laptop, and I decided to install ubuntu on my external hard drive.

After installation everytime my computer starts up it says "DEVICE NOT FOUND - a00s0fs78f76etc...

GRUB RECOVERY_"

I need to fix it so even without the external hard drive it just starts up as windows normally does!! I don't want a boot selection screen, I just installed ubuntu on external hard drive for practice and need help?..

Thanks!

---

### Post by Fir3chi3f on 2010-07-22
Haven't played around with windows 7, buy you should be able to boot off of your windows CD and 'fixmbr' in the recovery console:

```
fixmbr
```

I found that grub really doesn't like it when you take away its boot partition ;)

---

### Post by varunendra on 2010-07-22
To recover Win7 MBR, follow [this]("http://www.ehow.com/how_4836283_repair-mbr-windows.html").

To install Ubuntu on external drive, install it there as usual, only make sure that you install GRUB (via advance option) on the external drive instead of the fixed one.
Typically, your fixed drive would be "sda" and the external one should be "sdb". Just choose 'sdb' as destination for GRUB installation (remember- **sdb**, .....not sdb1, sdb2, etc.).
[An easy way to avoid confusion and any chance of mistake would be to remove the fixed hard drive before starting the installation]

---

### Post by MetaX on 2010-07-24
Anyway to do fixmbr without the dvd? I bought my windows online from micrsoft student store, so only have iso, and no dvd burner ;(

---

### Post by spydeyrch on 2010-07-24
I am assuming that you are still able to boot into ubuntu, right?

If you can get the Grub menu to work, with your external drive connected. You should be able to boot into win7. From there you have a couple options:

-You could install EasyBCD with has the option to recover your MBR and BCD. Thereby fixing your windows boot.

-You could use Microsoft's USB tool to make a bootable win7 USB and thereby boot from the USB thumb drive and fix your mbr.

Hopefully that helps. :D

-Spydey :KS

---

### Post by spydeyrch on 2010-07-24
> **MetaX said:**
> I have windows 7 on my laptop, and I decided to install ubuntu on my external hard drive.

After installation everytime my computer starts up it says "DEVICE NOT FOUND - a00s0fs78f76etc...

GRUB RECOVERY_"

I need to fix it so even without the external hard drive it just starts up as windows normally does!! I don't want a boot selection screen, I just installed ubuntu on external hard drive for practice and need help?..

Thanks!

Just a quick note:

Make sure your external USB HDD is connected.

From BIOS, set the external USB device as the first boot device in the boot sequence. This should then boot Grub and allow you to either boot Win7 or ubuntu. From there, boot into win7 and fix your MBR via one of the options I mentioned in my previous post.

Hopefully that works. :D

-Spydey :KS

---

### Post by spydeyrch on 2010-07-24
> **spydeyrch said:**
> I am assuming that you are still able to boot into ubuntu, right?

If you can get the Grub menu to work, with your external drive connected. You should be able to boot into win7. From there you have a couple options:

-You could install EasyBCD with has the option to recover your MBR and BCD. Thereby fixing your windows boot.

-You could use Microsoft's USB tool to make a bootable win7 USB and thereby boot from the USB thumb drive and fix your mbr.

Hopefully that helps. :D

-Spydey :KS

Just note that if you do this, fix your MBR/BCD, you won't be able to boot into ubuntu unless you reinstall it and, like varunendra mentioned, you isntall grub to your external usb HDD.

-Spydey :KS

---

### Post by linux18 on 2010-07-24
boot the live cd and type ```
 sudo grub-install /dev/sda && sudo update-grub  
```
no need to use the windows mbr, grub is just as good

---

### Post by spydeyrch on 2010-07-24
> **linux18 said:**
> boot the live cd and type ```
 sudo grub-install /dev/sda && sudo update-grub  
```no need to use the windows mbr, grub is just as good


Wouldn't this install GRUB onto sda (his windows drive)? I believe that the OP doesn't want to have a boot menu when he starts up his machine and wants it to boot just into his currently installed win7. ;)

> 
I need to fix it so even without the external hard drive it just starts  up as windows normally does!! I don't want a boot selection screen, I  just installed ubuntu on external hard drive for practice and need  help?..


True, this would allow him to boot to windows without the need of the external hdd connected. :D

-Spydey :KS

---

