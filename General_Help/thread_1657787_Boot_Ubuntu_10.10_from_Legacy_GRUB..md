---
title: "Boot Ubuntu 10.10 from Legacy GRUB."
date: 2011-01-01
forum: General Help
---

### Post by mbudden on 2011-01-01
Like the title states, I'm trying to boot Ubuntu 10.10 from Legacy GRUB. I have been with Ubuntu 9.04 for the longest time, haven't seen a reason to upgrade. But I had thought maybe I should try it out and see what's new. I installed it on a second HDD but it seems that 10.10 uses GRUB2 and not the old GRUB.

I've been searching for a way to be able to boot into Ubuntu 10.10 from Legacy GRUB with no success. I could press F12 and select my second HDD and be able to boot into it there. But that's just a PITA and would like if I could have it sitting in my Legacy GRUB menu. Any help would be great.

---

### Post by perspectoff on 2011-01-01
To chainload Grub2 (installed in this example in the /dev/sda7 partition) from Grub Legacy, use an entry of this format in the Grub Legacy menu.lst configuration file (stored in a boot partition, for example):

title Kubuntu Maverick OS (chainloader)
rootnoverify (hd0,6)
kernel /boot/grub/core.img

This assumes that you allowed Grub2 to be installed in the new partition along with your new OS. If you installed the new OS to /dev/sda7, for example, you must specify that Grub2 be installed only to /dev/sda7 and not to /dev/sda (which is the odd nomenclature the Ubuntu installer uses to indicate that it will install Grub2 to /dev/sda7 and then set the MBR to refer to /dev/sda7 in order to load Grub2 from there).

---

### Post by wilee-nilee on 2011-01-01
Grub2 is much easier once you get used to it.

---

### Post by mbudden on 2011-01-01
> **perspectoff said:**
> To chainload Grub2 (installed in this example in the /dev/sda7 partition) from Grub Legacy, use an entry of this format in the Grub Legacy menu.lst configuration file (stored in a boot partition, for example):

title Kubuntu Maverick OS (chainloader)
rootnoverify (hd0,6)
kernel /boot/grub/core.img

This assumes that you allowed Grub2 to be installed in the new partition along with your new OS. If you installed the new OS to /dev/sda7, for example, you must specify that Grub2 be installed only to /dev/sda7 and not to /dev/sda (which is the odd nomenclature the Ubuntu installer uses to indicate that it will install Grub2 to /dev/sda7 and then set the MBR to refer to /dev/sda7 in order to load Grub2 from there).

Interesting. Thanks for the speedy reply. I'll give this a try and post back results.

> **wilee-nilee said:**
> Grub2 is much easier once you get used to it.

I have no problem with learning something new. It's only the fact that my main HDD has my Ubuntu 9.04/Win7 install on it. I decided to give Ubuntu 10.10 a try and installed it on another HDD. Since my BIOS is set to boot from the 9.04/Win7 drive, I'd like to be able to select from Legacy GRUB to try out 10.10.

---

### Post by perspectoff on 2011-01-01
> **wilee-nilee said:**
> Grub2 is much easier once you get used to it.

I never said not to use Grub2. I said to chainload Grub2.

Grub2 is a PITA for a multi-boot system because it lives in the partition of only one OS and you have to keep track of which partition it is in and beware when the OS of that partition is changed. 

For any system with multiple OS's on it I still strongly recommend Grub Legacy in a boot partition, which is used only to chainload the bootloader of whichever OS is chosen. 

That way Windows can use its own bootloader, Mac OS X can use its own bootloader, and Ubuntu can use Grub2 (its own bootloader). There is no reason to force Grub2 down everyone's throat.

---

### Post by wilee-nilee on 2011-01-01
> **mbudden said:**
> Interesting.
I have no problem with learning something new. It's only the fact that my main HDD has my Ubuntu 9.04/Win7 install on it. I decided to give Ubuntu 10.10 a try and installed it on another HDD. Since my BIOS is set to boot from the 9.04/Win7 drive, I'd like to be able to select from Legacy GRUB to try out 10.10.

If you just set the 10.10 drive first you will see all 3 operating systems without any file editing most likely, that is the great part of grub2 the os-prober.

I never learned the grub-legacy stuff so I know how you feel though about using what works for you.:)

---

### Post by perspectoff on 2011-01-01
> **mbudden said:**
> It's only the fact that my main HDD has my Ubuntu 9.04/Win7 install on it. I decided to give Ubuntu 10.10 a try and installed it on another HDD. Since my BIOS is set to boot from the 9.04/Win7 drive, I'd like to be able to select from Legacy GRUB to try out 10.10.

Don't forget that the nomenclature in Grub Legacy for the first partition on a second HDD (i.e. /dev/sdb1) would be

(hd1,0)

instead of

(hd0,0) which refers to /dev/sda1

(or the (hd0,6), which refers to /dev/sda7, used in my example).

---

### Post by wilee-nilee on 2011-01-01
> **perspectoff said:**
> I never said not to use Grub2. I said to chainload Grub2.

Grub2 is a PITA for a multi-boot system because it lives in the partition of only one OS and you have to keep track of which partition it is in and beware when the OS of that partition is changed. 

For any system with multiple OS's on it I still strongly recommend Grub Legacy in a boot partition, which is used only to chainload the bootloader of whichever OS is chosen. 

That way Windows can use its own bootloader, Mac OS X can use its own bootloader, and Ubuntu can use Grub2 (its own bootloader). There is no reason to force Grub2 down everyone's throat.

Read my post as we posted at the same time.:rolleyes::rolleyes::rolleyes:

I would hardly say I'm forcing anything, this person has 10.10 on a second HD, bad blood here eh.

---

### Post by drs305 on 2011-01-01
There is a menu.lst example in Maverick at /usr/share/doc/grub/examples/menu.lst. You should be able to just copy that into your menu.lst file and make the necessary changes. If you have read about Grub2 at all, remember that Grub legacy counts both hard drives and partitions starting at 0.

The example looks like this, I've made it suitable for sdb1:

> title  Maverick
root (hd1,0)
linux /vmlinuz root=/dev/sdb1
#initrd /initrd.img

I don't know why they have the initrd line commented out. It looks wrong to me but compare it to your existing entries.

It's been a while since I've used Grub legacy. Just compare the above with what currently exists in your grub menu.lst file and paste it in. Of course you would probably have to manually add it again if grub is updated.

Personally, I'd suspect it would be something like this, but use the same format as what currently exists in your other entries.
> title  Maverick
root (hd1,0)
linux /boot/vmlinuz-2.6.35-24-generic root=/dev/sdb1 ro
initrd /boot/initrd.img-2.6.35-24-generic

---

### Post by mbudden on 2011-01-01
> **wilee-nilee said:**
> If you just set the 10.10 drive first you will see all 3 operating systems without any file editing most likely, that is the great part of grub2 the os-prober.

I never learned the grub-legacy stuff so I know how you feel though about using what works for you.:)

Yeah. I had noticed that when I selected the second HDD in BIOS. It's quite neat that it did that. It's nice to see things getting easier and easier. I've been playing around with Ubuntu since 7.04. So I've had much time to play around with the Legacy GRUB.

> **perspectoff said:**
> Don't forget that the nomenclature in Grub Legacy for the first partition on a second HDD (i.e. /dev/sdb1) would be

(hd1,0)

instead of

(hd0,0) which refers to /dev/sda1

(or the (hd0,6), which refers to /dev/sda7, used in my example).


> 
title Ubuntu 10.10 (chainloader)
rootnoverify (hd1,0)
kernel /boot/grub/core.img

That's how I have it set up. It takes me into the GRUB2 menu. Is there a way to bypass this? I'm assuming maybe by changing (hd1,1) or something?

> **drs305 said:**
> There is a menu.lst example in Maverick at /usr/share/doc/grub/examples/menu.lst. You should be able to just copy that into your menu.lst file and make the necessary changes. If you have read about Grub2 at all, remember that Grub legacy counts both hard drives and partitions starting at 0.

The example looks like this, I've made it suitable for sdb1:



I don't know why they have the initrd line commented out. It looks wrong to me but compare it to your existing entries.

It's been a while since I've used Grub legacy. Just compare the above with what currently exists in your grub menu.lst file and paste it in. Of course you would probably have to manually add it again if grub is updated.

Personally, I'd suspect it would be something like this, but use the same format as what currently exists in your other entries.

Thanks. I'll take a look and maybe try one of these solutions as well.

---

