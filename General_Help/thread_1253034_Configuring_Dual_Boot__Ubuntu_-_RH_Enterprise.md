---
title: "Configuring Dual Boot | Ubuntu - RH Enterprise |"
date: 2009-08-29
forum: General Help
---

### Post by Volguuz on 2009-08-29
Hi guys have a small challenge i'm trying to fix and am having some difficult, I hope you could lend me a hand.

I have currently installed 2 Linux versions - Kubuntu 9.04 and Red Hat Enterprise Linux 5. I know that by first installing RHEL and then Kubuntu i would have the problem solved but that is not an option for me since i don't want to reinstall Kubuntu and configure everything again.

So i am trying to configure the "menu.lst" to make this happen. Here is what i have done so far, i had RHEL 3 installed before ubuntu with ubuntu being on the first partition and RHEL on the second (both on the same HD) and at the time i did indeed reinstall kubuntu after so as to get this to work but now i would like to give a try at understanding how this works. 

I installed RHEL 5 on the same partition as the one before after formating it and chose not to install grub with it because i know it would screw the boot, so i began editing and this is what i have so far:


```
title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		56815c11-ff1f-4717-b27b-9b2ea6420996
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=56815c11-ff1f-4717-b27b-9b2ea6420996 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		56815c11-ff1f-4717-b27b-9b2ea6420996
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=56815c11-ff1f-4717-b27b-9b2ea6420996 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		56815c11-ff1f-4717-b27b-9b2ea6420996
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56815c11-ff1f-4717-b27b-9b2ea6420996 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		56815c11-ff1f-4717-b27b-9b2ea6420996
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=56815c11-ff1f-4717-b27b-9b2ea6420996 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		56815c11-ff1f-4717-b27b-9b2ea6420996
kernel		/boot/memtest86+.bin
quiet
```

This is the default stuff from Kubuntu, and then from the previous instalation of RHEL3:

```
# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Red Hat Enterprise Linux ES (2.6.18-12.EL) (on /dev/sda3)
uuid		0fefd8ef-c00e-490f-97c8-4ea448cfa807
kernel		/boot/vmlinuz-2.6.18-128.el5xen root=UUID=0fefd8ef-c00e-490f-97c8-4ea448cfa807 ro quiet splash
initrd		/boot/initrd-2.6.18-128.el5xen.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
#title		Red Hat Enterprise Linux ES-up (2.4.21-20.EL) (on /dev/sda3)
#root		(hd0,2)
#kernel		/boot/vmlinuz-2.4.21-20.EL ro root=LABEL=/ 
#initrd		/boot/initrd-2.4.21-20.EL.img
#savedefault
#boot
```

Now the second one is as it was before and the first was similar but i tried to change it to be similar to ubuntu by using the UUID instead of the "#root (hd0,2)" and on "Kernel" as well.

Problem is it cannot load the kernel even though the name of the file is written correctly. I get the Error 13: Invalid or unsupported executable format.

How can i make this work?

Thanks guys,
Ricardo.

---

### Post by Volguuz on 2009-08-30
bump.

---

