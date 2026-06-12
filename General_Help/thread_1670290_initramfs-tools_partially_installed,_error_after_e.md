---
title: "initramfs-tools partially installed, error after every use of apt-get/aptitude."
date: 2011-01-18
forum: General Help
---

### Post by tcopeland on 2011-01-18
Hello all. I was wondering how I can properly install initramfs-tools so it can properly configure boot images. You see, during **every** running of apt-get or aptitude processes, it returns this output after everything else has been installed/purged/removed/upgraded/etc. I've tried everything I can think of (which isn't much, I know): aptitude install, apt-get install, dpkg --configure, dpkg-reconfigure; and yet, it won't set up the image properly. Below is the output returned after every other package operation has been performed by apt-get or aptitude.
```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
cryptsetup: WARNING: found more than one resume device candidate:
                     /dev/sda2
                     UUID=48e81d9a-13f7-43a5-a7a4-6640fdca2eb6
.: 17: Can't open /etc/default/console-setup
E: /usr/share/initramfs-tools/hooks/console_setup failed with return 127.
update-initramfs: failed for /boot/initrd.img-2.6.35-24-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Any ideas?

---

