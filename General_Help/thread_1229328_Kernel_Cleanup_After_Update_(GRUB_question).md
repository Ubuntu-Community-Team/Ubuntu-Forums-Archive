---
title: "Kernel Cleanup After Update (GRUB question)"
date: 2009-08-02
forum: General Help
---

### Post by AxelMan0 on 2009-08-02
I recently installed Ubuntu 8.10 and shortly after it updated the kernel from 2.6.27-7-generic to 2.6.27-14-generic. I previously had the nvidia 185 series driver installed and I had to reinstall it after the kernel update. I was in a hurry however and did not properly purge the old install from my system. The driver appears to have installed properly but I was just wondering if there were any other things my computer may have left behind in the driver reinstall or kernel update?

Also, I have Jaunty installed on the first partition so I had to go into the menu.lst file in that partition and edit it to incorporate the new kernel version. When Jaunty updates this happens automatically. Currently Intrepid is underneath the ###automagic stuff. If I put the Intrepid entry in that group will it do everything automatically or will this not work because the menu.lst is on a different partition? If it's relevant I have Vista and it is NOT installed on the first partition, so it may be possible to install GRUB to the MBR (or is it already installed there?).

Here is the menu.lst stuff:

## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-14-generic
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet quiet splash 
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet  single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.04, kernel 2.6.28-13-generic
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet quiet splash 
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet  single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=8a59b1fa-3729-41ea-b2e2-970421d58ce5 ro clocksource=hpet  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        8a59b1fa-3729-41ea-b2e2-970421d58ce5
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Ubuntu 8.10, kernel 2.6.27-14-generic
uuid        b6a8cdce-ef21-4689-9a9d-4bc5e1f75fe1
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=b6a8cdce-ef21-4689-9a9d-4bc5e1f75fe1
initrd        /boot/initrd.img-2.6.27-14-generic
savedefault

title Windows Vista
root (hd0,1)
makeactive
chainloader +1
savedefault



edit: I found some info on update-grub. If I reinstall both Ubuntus with a shared /boot partition will that work automatically? I don't really care if I have to repartition/reinstall or anything I have all my important data on an external hard drive.

---

### Post by scouser73 on 2009-08-02
You should look at this tutorial on cleaning up old kernels: [[COLOR="Red"]**Removing Old Kernels**[/COLOR]]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/").

---

### Post by AxelMan0 on 2009-08-02
Cool I got rid of the old kernel :) Now how do I make grub automatically update the boot entry for intrepid? I always here people saying it's a good idea to share certain partitions. Is /boot one of them and is this why?

---

