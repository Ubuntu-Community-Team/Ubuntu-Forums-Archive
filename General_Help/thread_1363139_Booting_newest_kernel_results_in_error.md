---
title: "Booting newest kernel results in error"
date: 2009-12-24
forum: General Help
---

### Post by Hedley on 2009-12-24
I ran update manager today and when it (unusually) said "Not all updates can be installed", I made the apparent mistake of clicking on "Run a partial upgrade". 

The result is that now when I boot up, a small white Ubuntu logo sits on the screen for approximately three minutes and then the system drops to a command prompt labelled "(initramfs)". Searching this symptom seemed to suggest that there was some sort of disk error. 

However, this problem only happens when I select the most recent Linux kernel in Grub (that being "2.6.31-16-generic"). If I boot using either of the older kernels (-15 or -14), or if I boot the crappy Windows 7 that came with this laptop, everything works fine. 

I'm guessing that my partial upgrade may be the problem. But what to do to correct it? If I wait a while, will a subsequent upgrade solve the issues? Should I uninstall the problem kernel and reinstall it? If so, what is the best (ie: least complicated) way of doing so?

I'm using Ubuntu 9.10 AMD 64 on a Lenovo ThinkPad T400 that I bought a month ago. Installation was easy and flawless and everything worked perfectly out of the box, and I have had no other problems. 

Thanks for any advice!

---

### Post by adam814 on 2009-12-24
While using one of the running kernels:
> sudo update-initramfs -u -k 2.6.31-16-generic
My guess is the initrd image for the new kernel was not built properly during the update and this should rebuild it assuming the package itself installed properly.  If that doesn't work try:
> sudo dpkg-reconfigure linux-image-2.6.31-16-generic

---

### Post by sandy8925 on 2009-12-24
Hmmmm.....when I compiled the 2.6.31.6 kernel I using make-kpkg and installed it I found that no initrd.img file was created for it. But it still worked.

---

### Post by Hedley on 2009-12-24
Thanks for the reply, Adam814. 

While booted in 2.6.31-15, I tried your first suggestion, and this was the result:

> update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
W: Possible missing firmware /lib/firmware/e100/d102e_ucode.bin for module e100
W: Possible missing firmware /lib/firmware/e100/d101s_ucode.bin for module e100
W: Possible missing firmware /lib/firmware/e100/d101m_ucode.bin for module e100
cp: cannot stat `/lib/udev/hotplug.functions': No such file or directory


I then tried the second option, with the following result:

> Running depmod.
edward@bontano-thinkpad:~$ update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
W: Possible missing firmware /lib/firmware/e100/d102e_ucode.bin for module e100
W: Possible missing firmware /lib/firmware/e100/d101s_ucode.bin for module e100
W: Possible missing firmware /lib/firmware/e100/d101m_ucode.bin for module e100
cp: cannot stat `/lib/udev/hotplug.functions': No such file or directory
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.31-16.53 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.31-16.53 was configured last, according to dpkg)
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/nvidia-common

There has been no change in what happens when I try to boot 2.6.31-16.

---

### Post by dcstar on 2009-12-24
> **Hedley said:**
> I ran update manager today and when it (unusually) said "Not all updates can be installed", I made the apparent mistake of clicking on "Run a partial upgrade". 
........

That usually occurs because the repository you are using does not yet have all of the new packages, but it has the package list of them that the upgrade software uses. This usually occurs because the repository is misconfigured and does not comply to the Ubuntu standard that is meant to prevent this sort of thing.

You need to wait a day or so for all the updated packages to arrive, and then manually install them all:

```
**sudo apt-get update**
```

or run the Update Manager and do it that way.

---

