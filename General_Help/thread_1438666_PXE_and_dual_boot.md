---
title: "PXE and dual boot"
date: 2010-03-25
forum: General Help
---

### Post by wilsonmorgado on 2010-03-25
Hi. I have a Portege R100 laptop and it don't boot from Usb and not have a cd-rom drive. So, i only can install ubuntu / windows over PXE.


I install Ubuntu with pxe and it works fine. 

Now, i tried install windows xp, the setup copy the files to hdd and ask to restart.  But after restart the windows installation don't start! Start normal Ubuntu!


**How to force start Windows Xp installation **???


[COLOR="Orange"]Update 1:[/COLOR]

[COLOR="Indigo"]I have a /media/win/ folder under ubuntu with boot.ini file:[/COLOR]
> [Boot Loader]
Timeout=5
Default=C:\$WIN_NT$.~BT\BOOTSECT.DAT
[Operating Systems]
C:\$WIN_NT$.~BT\BOOTSECT.DAT = "Windows XP Installation/Upgrade"

[B]
I can add this to Grub ?[/B]




> wilson@vpn269:~$ sudo fdisk -l

Disk /dev/sda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000bac6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1215     9759456   83  Linux
/dev/sda2   *        1025        2431    11301727+   c  W95 FAT32 (LBA)
wilson@vpn269:~$ 



---

### Post by wilsonmorgado on 2010-03-25
**My own solution**

```
sudo update-grub
```

---

