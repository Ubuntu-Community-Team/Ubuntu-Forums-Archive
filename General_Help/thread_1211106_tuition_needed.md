---
title: "tuition needed"
date: 2009-07-12
forum: General Help
---

### Post by beacon on 2009-07-12
I have got a lot of help through these forums, but I have a couple of major problems that are too complicated, I think, to solve by email, and I can't find anyone who knows enough about Linux to give personal tuition. I have searched the web, looked in various computer sites, and written to Linux user groups (who don't even reply). I can find a good many people who offer help with Microsoft, but Linux is out-of-range. 

My problem is, essentially, that I can only boot Jaunty, even though I have tried to put another linux program on the hard drive (Puppy). It just isn't recognised. Another difficulty is that I want to boot from a USB flash drive, and the computer seems to allow it. However, it still boots only Jaunty.

I have consulted the young man who built the computer and who is a wizard when it comes to Windows, but he seems to have given up. Can anyone suggest a way to find someone willing to help on these problems that probably would take very little time? I would travel, but South Wales or the Marches would be the best locations.

---

### Post by bodyharvester on 2009-07-12
> **beacon said:**
> I have got a lot of help through these forums, but I have a couple of major problems that are too complicated, I think, to solve by email, and I can't find anyone who knows enough about Linux to give personal tuition. I have searched the web, looked in various computer sites, and written to Linux user groups (who don't even reply). I can find a good many people who offer help with Microsoft, but Linux is out-of-range. 

My problem is, essentially, that I can only boot Jaunty, even though I have tried to put another linux program on the hard drive (Puppy). It just isn't recognised. Another difficulty is that I want to boot from a USB flash drive, and the computer seems to allow it. However, it still boots only Jaunty.

I have consulted the young man who built the computer and who is a wizard when it comes to Windows, but he seems to have given up. Can anyone suggest a way to find someone willing to help on these problems that probably would take very little time? I would travel, but South Wales or the Marches would be the best locations.

you tried [www.howtogeek.com](www.howtogeek.com) yet?

good luck

---

### Post by issih on 2009-07-12
If the computer allows it, then booting from usb is a simple case of setting bios correctly, jaunty should not get anywhere near booting.

You need to go into bios and set the boot order so that the usb drive is checked as a boot device ahead of the hard drive.

As for getting puppy to boot from the hard drive, that is a case of adding the appropriate section to grub.

Hope that helps

---

### Post by GCoffee on 2009-07-12
Never used puppy linux myself, but could it be conflicting bootloaders? Grub and Lilo?

---

### Post by beacon on 2009-08-16
Message repeated below.

---

### Post by beacon on 2009-08-16
I apologise to the three people who offered advice. As a relative newcomer to the forum I thought I would be notified of any replies and only just discovered your messages when I accidentally came across them this morning. I appreciate your advice and suggestions.

It would seem to be a matter of  getting the boot sequence right, and I have tried several times. I wonder if it would help if I give the following information:

IDE primary master      DVDRW IDE H16X
IDE primary slave        Maxtor STM 3160
Sata1                           Maxtor STM3160

Boot Sequence:

1st boot device           USB: USB CF
2nd boot device          CD/DVD: PM-DVDR
3rd boot device           Sata: 3m-Maxtor

Hard Disk Drives

1st                               Sata: 3M-Maxtor
2nd                              HDD: PS-Maxtor

Removable Drives

1st                               USB: USB CF
2nd                              USB: USB MS
3rd                               USB: USB SD
4th                               USB:USB SM

I'm getting nowhere with finding tuition, so all help is appreciated.

---

### Post by 3rdalbum on 2009-08-16
1. Try reinstalling GRUB, so it will detect Puppy and Ubuntu and make sure both are in the boot menu: [http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")

2. Try downloading "Unetbootin" and using that to turn a live CD image into a live USB. *Unetbootin* does things a bit differently to *USB Startup Disk Creator*, and it seems to work with more machines than USDC.

---

### Post by beacon on 2009-08-16
Thank you 3rdalbum. The first suggestion was very helpful. I don't want to impose, but couldyou possibly give me step-by-step instructions re netbooting. Rather,  I have typed in 'puppy' and ticked diskimage iso. Then I am asked for the drive, but have no idea what I should use. Using fdisk, I get the following information, but I'm not certain what it all means:

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19272   154802308+  83  Linux
/dev/sda2           19273       19457     1486012+   5  Extended
/dev/sda5           19273       19457     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77777777

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1019     8185086   83  Linux
/dev/sdb2            1020       19457   148103235    5  Extended
/dev/sdb5            1020        1528     4088511   82  Linux swap / Solaris
/dev/sdb6            1529        1594      524288   83  Linux
/dev/sdb7   *        1594        1619      204799+  83  Linux
/dev/sdb8            1619       19457   143285572 8e Linux LVM

Many thanks.

---

### Post by scouser73 on 2009-08-16
I think that the boot sequence: 
> 1st boot device USB: USB CF
2nd boot device CD/DVD: PM-DVDR
3rd boot device Sata: 3m-Maxtor

Should be, 

1st boot device CD/DVD: PM-DVDR
2nd boot device USB: USB CF
3rd boot device Sata: 3m-Maxtor

The reason for this is that once the CD is in the drive, the drive will be accessed first thus enabling you to install your distro of choice.

---

### Post by beacon on 2009-08-17
Thanks scouser. I hae changed the settings but it makes no difference. However (even before the change) I managed to get the screen to show both Ubuntu and Pclos, which I had tried to install before but thought had been unsuccessful.

---

