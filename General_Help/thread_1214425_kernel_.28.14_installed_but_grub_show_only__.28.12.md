---
title: "kernel .28.14 installed but grub show only  .28.12"
date: 2009-07-15
forum: General Help
---

### Post by DougieFresh4U on 2009-07-15
I have mentioned this issue before and didn't get any resolution and with kernel update today, still not resolving.
The issue is: My machine is a triple boot and my 'grub' list things is this order, simply put;
karmic
Win 7
Jaunty
mem test
Under the 'Jaunty' is the kernels
.28.12
.28.11
Ok, so when update came awhile back and kernel went to '.28.13', my 'grub' didn't show '.28.13'. Synaptic shows it's installed. Today update moved kernel to '.28.14' and Synaptic showing installed but 'grub' is still only showing '.28.12'
uname -r shows the .28.12 
What is going on here? Why are the other newer kernel updates not in 'grub'? Can some one please help me track this down? Things to check?
I will post whatever, please give commands and I will post any more info needed to get this booting to newest kernel upgrade.
Thanks

---

### Post by DougieFresh4U on 2009-07-16
Any ideas please?

---

### Post by csabo2 on 2009-07-16
Try manually adding it and see what happens.

---

### Post by DougieFresh4U on 2009-07-16
> **csabo2 said:**
> Try manually adding it and see what happens.

When I go into '**boot/grub/menu.lst**', it shows its SUPPOSED to be there, but when starting machine and grub comes up, it's not there. Only '.28.11' and '.28.12' are there for me to chose to boot
```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		b3d866ba-af4a-4234-9a91-03d360a738f0
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro quiet splash vga=794  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		b3d866ba-af4a-4234-9a91-03d360a738f0
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		b3d866ba-af4a-4234-9a91-03d360a738f0
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro quiet splash vga=794  crashkernel=384M-2G:64M@16M,2G-:128M@16M
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		b3d866ba-af4a-4234-9a91-03d360a738f0
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro  crashkernel=384M-2G:64M@16M,2G-:128M@16M single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-12-generic
uuid		b3d866ba-af4a-4234-9a91-03d360a738f0
kernel		/boot/vmlinuz-2.6.28-12-generic root=UUID=b3d866ba-af4a-4234-9a91-03d360a738f0 ro quiet splash vga=794  crashkernel=384M-2G:64M@16M,2G-:128M@16M
```

---

### Post by philinux on 2009-07-16
The reason is where grub is installed. When I started looking at dual booting I realised this would occur. When I install to my second hard drive I use the advanced button at the end of the installation and ask it to install grub to the partition and not the disc. Then from system on first hard drive I use this in grub. 
This method stops the second install from grabbing grub off my first hard drive. 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title        SDB Karmic
configfile   (**hd1,0**)/boot/grub/menu.lst

You could try using ```
sudo update-grub
``` to see if that sorts out your menu.lst with the new kernel.

---

### Post by DougieFresh4U on 2009-07-16
> **philinux said:**
> The reason is where grub is installed. When I started looking at dual booting I realised this would occur. When I install to my second hard drive I use the advanced button at the end of the installation and ask it to install grub to the partition and not the disc. Then from system on first hard drive I use this in grub. 
This method stops the second install from grabbing grub off my first hard drive. 
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title        SDB Karmic
configfile   (**hd1,0**)/boot/grub/menu.lst

You could try using ```
sudo update-grub
``` to see if that sorts out your menu.lst with the new kernel.

Thanks, will try that when I boot back into Jaunty.
here pic of 'grub' during boot-up

---

