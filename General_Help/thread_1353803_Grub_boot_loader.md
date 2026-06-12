---
title: "Grub boot loader"
date: 2009-12-13
forum: General Help
---

### Post by luftadler on 2009-12-13
Hi,

I have a problem with GRUB BOOT LOADER, after update it add to the boot menu  another Ubuntu version. So, now i have like 6 versions of Ubuntu plus Windows XP.
How can I edit the GRUB BOOT LOADER to delete unnecessary versions of Ubuntu from the boot menu. :confused:


Thank you!

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
[Let me google that for you...]("http://lmgtfy.com/?q=remove+old+kernels+ubuntu")

---

### Post by garvinrick4 on 2009-12-13
Do you mean six versions of the Linux Kernel?

---

### Post by Leppie on 2009-12-13
Remove some of the older kernel images and headers in synaptic.
Then update grub:
```
$sudo update-grub
```

The older entries will disappear.

---

### Post by luftadler on 2009-12-15
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
thank you...

---

### Post by luftadler on 2009-12-15
>  				 				**Re: Grub boot loader** 			
 			 			 		   		 		 		Do you mean six versions of the Linux Kernel?
 		                   		  		  		 		 			 				__________________
				Remember hence where you come and pass it down. 			

no just 3, but was doubled by safe mode version of each

---

