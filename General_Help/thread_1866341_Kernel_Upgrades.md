---
title: "Kernel Upgrades"
date: 2011-10-21
forum: General Help
---

### Post by jim_deadlock on 2011-10-21
I have an i7 with 8G RAM and I now have kernel version 3.0.0-12 in Ubuntu 11.10 (64 bit). I have another older machine with a P4 and 1G RAM running Ubuntu 32 bit and when I upgraded it from 11.04 to 11.10 it is still running 2.6.35-25 kernel, is this because of the lesser hardware or because it's 32 bit? I'm not too bothered, just curious.

---

### Post by zvacet on 2011-10-21
Kernel version is dependent of Ubuntu version ,not architecture.On your old comp run

```
lsb_release -a
```

to be sure witch version you are running.If it is 11.10 the try with 


```
sudo update-grub
```

You should run kernel 3 no matter witch architecture  you are using.

---

### Post by jim_deadlock on 2011-10-21
```
$ lsb_release -a
LSB Version:	core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric

$ sudo update-grub
[sudo] password for jim: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.0.0-12-generic
Found kernel: /boot/vmlinuz-2.6.35-25-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... Updating the default booting kernel
done
```

I checked menu.lst after this and the 3.0.0 kernel is listed there properly. However, when I reboot the new kernel is still not showing on the GRUB menu.

---

### Post by jim_deadlock on 2011-10-22
I've made a new discovery. When I run sudo update-grub my /boot/grub/grub.cfg file is not being updated, it's 9 months old:

```
-r--r--r-- 1 root root 4368 2011-02-02 02:16 /boot/grub/grub.cfg
```

I compared the permissions with the file on my other computer and it looks like it's supposed to be read-only like that, so why is it not being updated...?

---

### Post by jim_deadlock on 2011-10-22
OK I've solved my immediate problem by running

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

... and now my new kernel is showing properly in GRUB. However, I'll still need to keep doing this manually in the future unless I can find a way to fix it properly so that the kernel can be updated by general system updates etc. Do I need to completely purge and reinstall GRUB or can someone offer an easy fix? I'm wary about messing with GRUB unless it's essential.

---

### Post by CharlesA on 2011-10-22
What version of grub are you using? menu.lst was used in grub 0.97 IIRC.

---

### Post by jim_deadlock on 2011-10-22
GRUB2 version 1.98

---

