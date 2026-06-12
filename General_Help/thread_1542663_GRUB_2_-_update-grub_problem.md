---
title: "GRUB 2 - update-grub problem"
date: 2010-07-30
forum: General Help
---

### Post by zylvere on 2010-07-30
Hello! 

I'm having a problem with GRUB2: 

Whenever I run "update-grub" or "update-grub2" (I suspect this is the same file), it doesn't mention the fact that I have no 05_debian_theme file. When I add this file, it doesn't pay attention to it:  i.e. doesn't list it. 

Here is a snapshot of my "update-grub2":
root@zylvere-laptop:~# update-grub2
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found Windows 7 (loader) on /dev/sda2
done

It should be trying to use a background as part of the GRUB system. 

Any ideas? 

Many thanks in advance!!

---

### Post by dcstar on 2010-07-31
> **zylvere said:**
> Hello! 

I'm having a problem with GRUB2: 

Whenever I run "update-grub" or "update-grub2" (I suspect this is the same file), it doesn't mention the fact that I have no 05_debian_theme file. When I add this file, it doesn't pay attention to it:  i.e. doesn't list it. 
.........

Look at the /boot/grub/grub.cfg file that is generated.

---

