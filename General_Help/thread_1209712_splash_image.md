---
title: "splash image"
date: 2009-07-10
forum: General Help
---

### Post by theo.ew on 2009-07-10
theo@theo-laptop:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done


This is what happens when I run the above command. I followed the instructions at this link to make my startup faster([http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html](http://its-about-amoena.blogspot.com/2007/12/how-to-make-ubuntu-to-start-faster.html))

I followed the instructions and it disabled the splash screen and didn't help the startup time at all. I would like to get the splash screen back now. Any ideas?

---

### Post by pennacook on 2009-07-10
Add the word ```
splash
``` back to the end of the kernel line and reboot. This should take care of it.

---

### Post by theo.ew on 2009-07-10
if you noticed that site also told me to install a program that ran from the terminal and let you disable stuff. There were some X's I unclicked and I'm not sure what the default setting for those are. (This will make much more sense if you actually install and run the program. 

I added the word "splash" to the file and it didn't change anything.

---

