---
title: "backports error"
date: 2009-11-10
forum: General Help
---

### Post by Vaxon on 2009-11-10
I'm going to start from the beginning
I reinstalled kubuntu jaunty after a bad incident with 9.10(not going to get into)
and I was installing all of the upgrades
4 upgrades were blocked
and I got an idiotic idea to install them through the terminal
they installed perfectly
but when I restarted my laptop couldn't use wireless
So I connected it to the internet through an ethernet cable
I did a little googling and found something about installing "linux-backports-modules-2.6.28-16-generic" I tried to install it an error occured and that didn't work
later I read somewhere else telling someone to boot into their previous kernel 
I tried that and my wireless worked perfectly
I figured out how to make my previous kernel the default for when I turn on my laptop
But later I tried to install something
most of the installation will go perfectly until the end where it will try to install the "linux-backports-modules-2.6.28-16-generic" again and this happens
```

Setting up linux-backports-modules-2.6.28-16-generic (2.6.28-16.18) ...
Bus error
update-initramfs: Generating /boot/initrd.img-2.6.28-16-generic
Segmentation fault
update-initramfs: failed for /boot/initrd.img-2.6.28-16-generic
dpkg: error processing linux-backports-modules-2.6.28-16-generic (--configure):
 subprocess post-installation script returned error exit status 1

```After that the program continues to install normally
but it takes up to 10 minutes to get past the "Setting up linux-backports-modules-2.6.28-16-generic (2.6.28-16.18 ) ...
Bus error" part greatly increasing the install time of the program
I tried "sudo apt-get remove linux-backports-modules-2.6.28-16-generic"
but it was unable to uninstall it

which brings me here

---

### Post by cambunctious on 2009-11-11
I have a somewhat similar problem with the same package. I upgraded to Ubuntu 9.10 and then removed some unneeded packages. When I try to completely remove linux-backports-modules-2.6.28-16-generic I get this error:

E: linux-backports-modules-2.6.28-16-generic: subprocess installed post-removal script returned error exit status 1

---

