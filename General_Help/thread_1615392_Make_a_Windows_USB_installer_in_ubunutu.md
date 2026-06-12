---
title: "Make a Windows USB installer in ubunutu"
date: 2010-11-06
forum: General Help
---

### Post by penguin1029 on 2010-11-06
hello, 
i need some help 
i need to make a windows xp install drive in ubuntu 
any suggestions?

---

### Post by Jechem on 2010-11-06
I've tried everything I can think of and gave up on it. Ubuntu 10.04 has done everything I need so far. I'd be interested also if you find a solution to this old problem. Good luck. ;)

---

### Post by Hakunka-Matata on 2010-11-07
what is the problem?  What prevents you from using unetbootin to make a bootable USB Drive as long as you have a windows iso file available to supply to unetbootin program?

---

### Post by sikander3786 on 2010-11-07
> **Hakunka-Matata said:**
> what is the problem?  What prevents you from using unetbootin to make a bootable USB Drive as long as you have a windows iso file available to supply to unetbootin program?
I don't think unetbootin will ever be able to create a Windows XP startup disk as Windows is not a Linux Distro and that is what unetbootin is intended for.

---

### Post by Verbeck on 2010-11-07
you could try[ wintoflash]("http://wintoflash.com/home/en/") in wine, but i'm not sure whether it would work

---

### Post by Kr0nZ on 2010-11-07
ive used the windows version of unetbootin to create windows boot usb, im not sure about the ubuntu version but i see no reason why it shouldn't work as long as you have the windows iso.. 
i shall give it a try and report back

---

### Post by Jechem on 2010-11-07
> **Verbeck said:**
> you could try[ wintoflash]("http://wintoflash.com/home/en/") in wine, but i'm not sure whether it would work

wintoflash has errors in wine. it gets stuck after you select the windows files/iso.

---

### Post by Jechem on 2010-11-07
> **Kr0nZ said:**
> ive used the windows version of unetbootin to create windows boot usb, im not sure about the ubuntu version but i see no reason why it shouldn't work as long as you have the windows iso.. 
i shall give it a try and report back

I've tried that before and I can't get thru the menu. The linux unetbootin creates syslinux so it can't load the windows bootloader.

---

### Post by wilee-nilee on 2010-11-07
This works for me, take a thumb drive delete the partitioning with gparted put a ntfs back in and put the boot flag on it. Take a W7 ISO and use the archive manager to extract it to the thumb, reboot and it works for me.

Oops missed the XP part, okay here is how I load XP to a thumb.  

First make a virtual running XP then use this to load a thumb has worked every time. use the link in post 5 or run it in wine I guess. The problem here is that it has to be a legit copy of XP for this tool to work.

---

