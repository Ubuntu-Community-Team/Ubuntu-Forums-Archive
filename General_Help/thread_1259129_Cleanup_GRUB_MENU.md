---
title: "Cleanup GRUB MENU"
date: 2009-09-05
forum: General Help
---

### Post by sandman3838 on 2009-09-05
Hello

My GRUB menu has the following listings.
I would like to shrink it down a bit and just leave the last two updates.
I'm a little worried about dong this.  I so don't want any issues.
What lines should I delete or should I just use #?

## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-13-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/memtest86+.bin
quiet



Thank you all for your help.

---

### Post by coldReactive on 2009-09-05
check to see if those kernels are installed first, usually you can search them out in synaptic with linux-image or something.

---

### Post by starcraft.man on 2009-09-05
> **sandman3838 said:**
> Hello

My GRUB menu has the following listings.
I would like to shrink it down a bit and just leave the last two updates.
I'm a little worried about dong this.  I so don't want any issues.
What lines should I delete or should I just use #?

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/memtest86+.bin
quiet

```


Thank you all for your help.

Voila. If ya don't have any issues with 15, can just comment out 14 like so:

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

#title		Ubuntu 9.04, kernel 2.6.28-14-generic
#uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
#kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro quiet splash 
#initrd		/boot/initrd.img-2.6.28-14-generic
#quiet

#title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
#uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
#kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=7a303972-2c9e-44b0-9904-dedeefdc6cf8 ro  single
#initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, memtest86+
uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
kernel		/boot/memtest86+.bin
quiet

```

Commenting (# in front of line) has effect of removing it from menu displayed at GRUB, but leaving it in file if trouble. Also, be sure to manually remove them via synaptic, look for linux-image or 2.6.28 in search and they ought pop up for removal.

Or:

```
sudo apt-get autoremove
```
Some people apparently I've been told, had autoremove do not so great things...

Also, I'm told there is a GUI called startupmanager (that's package name in repos too if ya want to install) that handles this kinda thing. Who uses a GUI though? :P

---

### Post by coldReactive on 2009-09-05
autoremove doesn't remove them from the grub list.

---

### Post by ronparent on 2009-09-05
The # in front of any title line should cancel loading of that kernel. It's also easily undone and less permanent should you want to later restore any booting options. Note: that edit has to be as admin and initiated from the terminal - ie enter **gksudo gedit /boot/grub/menu.lst**. Save and exit after your edit.

---

### Post by starcraft.man on 2009-09-06
> **coldReactive said:**
> autoremove doesn't remove them from the grub list.

I know that, never said it did. autoremove is merely an automated way of removing deprecated or unused packages. 

Also yes, good of you to point ron, need root power of course to make changes to GRUB, edit as he says. Gedit with root power works, or whatever ya like for editting.

---

### Post by sandman3838 on 2009-09-06
Cool

First the Kernals are there and working.

You see I almost did it without asking you all!
I'm so glad I did!

I knew # would work but I wasn't sure what to block?

I almost did this with the other stuff above it.....

#title		Ubuntu 9.04, memtest86+
#uuid		7a303972-2c9e-44b0-9904-dedeefdc6cf8
#kernel		/boot/memtest86+.bin
#quiet

I'm so glad I asked!   Thank you!  Thank you!

---

### Post by lswb on 2009-09-06
You can uninstall the older kernels using synaptic. Start synaptic and use the search function for example to look for "2.6.28-11-generic" Each kernel will usually have 3 packages marked as installed, one for the kernel itself, one for the headers, and one for restricted modules. Mark all 3 for removal or "complete removal". Repeat with any other kernel versions you want to uninstall, then click on apply. The grub menu will be updated automatically as part of this process.

---

