---
title: "grub load menu list"
date: 2010-06-28
forum: General Help
---

### Post by mohammed85 on 2010-06-28
Hi,

I have upgraded to Ubunto 10.4 a while ago but why it is still showing 9.10 in the menu list when I load?? moreover I have have done the same in the linux kernel I am trying to upgrade to 2.6.32 when I do this sudo update-grub I get the following

Found kernel: /boot/vmlinuz-2.6.32-020632-generic
Found kernel: /boot/vmlinuz-2.6.32-22-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-9-generic
Found kernel: /boot/vmlinuz-2.6.24-22-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


I can see them all apart from the first one when the computer starts?

Any idea why it is still showing 9.10 while it is 10.4 and why I can not choose 2.6.32?

---

### Post by Leppie on 2010-06-28
could you please download and run the [boot info script]("http://sourceforge.net/projects/bootinfoscript/") and post the complete output here?

---

### Post by mohammed85 on 2010-07-02
I have managed to update the list by updating the kernel from the Synaptic and selecting the first option rather than the default second one.

---

