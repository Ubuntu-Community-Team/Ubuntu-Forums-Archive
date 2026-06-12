---
title: "linux-image &amp; grub-pc errors Bug 686639"
date: 2010-12-18
forum: General Help
---

### Post by masque7 on 2010-12-18
```
Errors were encountered while processing:
 linux-image-2.6.32-26-generic
 grub-pc
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up grub-pc (1.98-1ubuntu9) ...
/etc/default/grub: 10: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up linux-image-2.6.32-26-generic (2.6.32-26.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-26-generic
Running postinst hook script /usr/sbin/update-grub.
/etc/default/grub: 10: splash: not found
User postinst hook script [/usr/sbin/update-grub] exited with value 127
dpkg: error processing linux-image-2.6.32-26-generic (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-26-generic; however:
  Package linux-image-2.6.32-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.26.28); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-pc
 linux-image-2.6.32-26-generic
 linux-image-generic
 linux-generic
```Any ideas why it's causing me grief? Strangely, my package manager works fine (as in downloads/installs packages).

I've searched the forum -- nothing seems to be solved, and I've also reported this as a bug. Bug 686639 is a duplicate of:
> *** This bug is a duplicate of bug 484499 ***
    [https://bugs.launchpad.net/bugs/484499](https://bugs.launchpad.net/bugs/484499)Turns out that netbook/laptop users who've added the acpi_backlight vendor option to /etc/default/grub to try and deal with brightness issues now suffer from this dependency issue

---

### Post by dcstar on 2010-12-18
> **masque7 said:**
> Any ideas why it's causing me grief? Strangely, my package manager works fine (as in downloads/installs packages).

```
A package failed to install. Trying to recover:
Setting up grub-pc (1.98-1ubuntu9) ...
**/etc/default/grub: 10: splash: not found**
dpkg: error processing grub-pc (--configure):
```
........
Turns out that netbook/laptop **users who've added the acpi_backlight vendor option to /etc/default/grub** to try and deal with brightness issues now suffer from this dependency issue

[LIST=1]
[*]Do not quote code.
[*]**Someone** has corrupted the Grub config so it cannot run.
[/LIST]

---

