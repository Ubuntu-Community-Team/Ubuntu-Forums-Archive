---
title: "update-grub: to much entries found?"
date: 2010-07-15
forum: General Help
---

### Post by Menelaos on 2010-07-15
My systems hosts 10.04 (installed first) and a Windows 7 (installed second).

When I do "update-grub" it results

[FONT=Courier New]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda3
done[/FONT]

Where come these multiple entries from and how to remove?

---

### Post by dino99 on 2010-07-15
you have 3 kernels installed: 32-21/22/23

its a good idea to have 2 kernels installed in case one have issue

to remove the older one ( 32-21) goto synaptic and remove all 21 related packages (header & image)

---

### Post by Menelaos on 2010-07-16
> **dino99 said:**
> you have 3 kernels installed: 32-21/22/23

its a good idea to have 2 kernels installed in case one have issue

to remove the older one ( 32-21) goto synaptic and remove all 21 related packages (header & image)


SOLVED: Thank you guys! :D

---

### Post by Oldhacker on 2010-07-18
> **Menelaos said:**
> SOLVED: Thank you guys! :D

I have six other entries in my GRUB menu for Ubuntu 10.04
Two are from another OS (openSUSE) and four from previous versions of Ubuntu. They are all found with "update-grub."
This makes for a very cluttered boot screen.

Going into Synaptic Package Manager as per this post, my search can fined NONE of them for me to delete!

What have I missed?

Thank you

---

