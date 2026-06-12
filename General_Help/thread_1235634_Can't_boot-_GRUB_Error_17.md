---
title: "Can't boot- GRUB Error 17"
date: 2009-08-09
forum: General Help
---

### Post by chrisxuk on 2009-08-09
Hi there,
 
 I need some help :( 
 Basically, just installed Ubuntu and when i restart now i get an error

It says GRUB Loading, please wait...
Error 17

and doesn't get any further :(

What has gone wrong? :( Please help :p

Thanks in advance
Chris

---

### Post by Barafu Albino Cheetah on 2009-08-09
Grub did not find your kernel. if you really _just_ installed ubuntu, the best idea for novice is to simply reinstall.

---

### Post by chrisxuk on 2009-08-09
Hi there,
I can't even get to Windows though. Am i going to have to reinstall that as well?

Chris

---

### Post by Barafu Albino Cheetah on 2009-08-09
You have messed windows NTloader, but hopefully, not it's file part. First, try to reinstall Ubuntu. May be it will find Windows and add it to Ubuntu's bootloader.

---

### Post by Narada on 2009-08-09
+1 the reinstallation thing. GRUB should auto-detect your Windows partition and add it to the boot menu. If it doesn't and you know the Windows partition number you can edit the grub menu yourself. Example:
```
sudo nano /boot/grub/menu.lst
```
```
timeout   10
default   0
color green/black yellow/green

# (0) Arch Linux
title  Arch Linux
root   (hd0,5)
kernel /vmlinuz26 root=/dev/disk/by-uuid/21505826-adb5-4c95-88dc-578cd3265747 ro vga=866 resume=/dev/sda3
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,5)
kernel /vmlinuz26 root=/dev/disk/by-uuid/21505826-adb5-4c95-88dc-578cd3265747 ro
initrd /kernel26-fallback.img

# (2) Windows
title Micro$oft Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
```
Windows was installed before Linux in the example above - which is probably how yours is - so you can see its partition location of hd0,0. (The first 0 being the first physical drive and second 0 being the first partition on the disk.) When you select this option from the actual GRUB menu GRUB knows what partition Windows is on and lets the Windows bootloader take over from there.

Did you by chance edit your menu.lst while trying to get things to dual boot? If you made a typo on your kernel line for Ubuntu that would explain your GRUB error 17. (Note: Your menu.lst may not use UUIDs. Don't worry if it looks different.)

---

### Post by chrisxuk on 2009-08-09
Hi there,

Would i be able to get rid of this problem if i were to install XP again then use partition magic to format everything else?

Thanks
Chris

---

### Post by Narada on 2009-08-09
> **chrisxuk said:**
> Hi there,

Would i be able to get rid of this problem if i were to install XP again then use partition magic to format everything else?

Thanks
Chris

Aye. The Windows install will overwrite GRUB. You can try again with the Ubuntu install as many times as you want, or just use Partition Magic to delete the Linux partitions and regain their free space for XP.

---

### Post by Bucky Ball on 2009-08-09
Just edit the grub menu.lst as suggested in previous post. Windows is no doubt on (hd0,0) so just point the grub entry for Windows to (hd0,0)

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windoze Vista - Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```It is easy and you will save yourself a heap of time plus learn a little about Ubuntu in the process (and there is a learning curve usually). You can use the Live CD to achieve this. :)

You are too close to start at the beginning again.

ps: Install Windows and use Partition Magic? Waste of time. You would install Windows on the first partition and leave the rest free space. Ubuntu will take care of that or you can manually partition it during install.

---

### Post by Narada on 2009-08-09
> **Bucky Ball said:**
> ps: Install Windows and use Partition Magic? Waste of time. You would install Windows on the first partition and leave the rest free space. Ubuntu will take care of that or you can manually partition it during install.

Right, but if he just wanted Windows and wanted to give up on Ubuntu that would be fine. Though now that I think about it he could simply have XP delete and format those partitions so you're right, PM is unneeded.

---

### Post by chrisxuk on 2009-08-09
> **Narada said:**
> +1 the reinstallation thing. GRUB should auto-detect your Windows partition and add it to the boot menu. If it doesn't and you know the Windows partition number you can edit the grub menu yourself. Example:
```
sudo nano /boot/grub/menu.lst
``````
timeout   10
default   0
color green/black yellow/green

# (0) Arch Linux
title  Arch Linux
root   (hd0,5)
kernel /vmlinuz26 root=/dev/disk/by-uuid/21505826-adb5-4c95-88dc-578cd3265747 ro vga=866 resume=/dev/sda3
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,5)
kernel /vmlinuz26 root=/dev/disk/by-uuid/21505826-adb5-4c95-88dc-578cd3265747 ro
initrd /kernel26-fallback.img

# (2) Windows
title Micro$oft Windows
rootnoverify (hd0,0)
makeactive
chainloader +1
```Windows was installed before Linux in the example above - which is probably how yours is - so you can see its partition location of hd0,0. (The first 0 being the first physical drive and second 0 being the first partition on the disk.) When you select this option from the actual GRUB menu GRUB knows what partition Windows is on and lets the Windows bootloader take over from there.

Did you by chance edit your menu.lst while trying to get things to dual boot? If you made a typo on your kernel line for Ubuntu that would explain your GRUB error 17. (Note: Your menu.lst may not use UUIDs. Don't worry if it looks different.)

Hi there,
Could you, or someone else please explain a little further about what to do once i have put this into the terminal:
```
sudo nano /boot/grub/menu.lst
```

Thanks
Chris

---

### Post by Narada on 2009-08-09
> **chrisxuk said:**
> Hi there,
Could you, or someone else please explain a little further about what to do once i have put this into the terminal:
```
sudo nano /boot/grub/menu.lst
```

Thanks
Chris

What exactly is it that you want to do? Reinstall XP and then reinstall Ubuntu, or just reinstall XP and leave Linux alone? If you're going to reinstall stuff you actually don't need to bother editing menu.lst as GRUB will be overwritten during the process.

---

### Post by chrisxuk on 2009-08-09
Hi there,
problems solved now. I formatted the partitions except XP, then used the XP recovery disk to make a new bootsector with FIXMBR  

Now, i can reinstall Ubuntu and hopefully won't have anymore problems. :)

Regards
Chris

---

