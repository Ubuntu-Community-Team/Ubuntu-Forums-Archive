---
title: "Old Kernel Compile errors resurface"
date: 2010-03-02
forum: General Help
---

### Post by liferules on 2010-03-02
I tried to compile a custom kernel a few months ago and I was unsuccessful. That is not the source of this post, but I un-installed all packages that I downloaded and removed all references to the attempted kernel and I thought it was over.

Today I tried to install xubuntu-desktop and the install exits with a dpkg errros that refers to that old custom kernel attempt. I run dpkg as instructed (see below):

```

chuck@chimera:~$ sudo dpkg --configure -a
[sudo] password for chuck: 
Setting up initramfs-tools (0.92bubuntu53) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32.8-some-string-here
Cannot find /lib/modules/2.6.32.8-some-string-here
update-initramfs: failed for /boot/initrd.img-2.6.32.8-some-string-here
dpkg: subprocess installed post-installation script returned error exit status 1

```

I cannot run apt-get until I try to figure out where this error is. Can someone provide some help?

---

### Post by liferules on 2010-03-02
Never mind I found the answer here:

[http://ubuntuforums.org/showthread.php?t=1005049](http://ubuntuforums.org/showthread.php?t=1005049)

---

