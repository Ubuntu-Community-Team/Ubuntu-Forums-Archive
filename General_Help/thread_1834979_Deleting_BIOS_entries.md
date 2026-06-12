---
title: "Deleting BIOS entries"
date: 2011-08-28
forum: General Help
---

### Post by 00ps on 2011-08-28
Hi,

I'm just wondering if having duplicate entries of Ubuntu in the BIOS is normal? I'm abit of an ocd freak about this type of thing, is there a way remove them?

I'm quite the newbie to Linux but I really like it. I started my PC with a clean install of Win7, then I tried Ubuntu via Wubi. Once I realised I wanted Ubunutu as a permanent OS I removed the Wubi version, bought another hard drive and split it in half. Half for Win7 and half for a fresh install of Ubuntu. 

Sorry if this is a really simple problem to sort out, I tried using bcdedit to remove the entries but Windows can't see it.

---

### Post by kartabosh on 2011-08-28
first of all, that's not the bios, that's called a bootloader 
if you want to remove entries you will either have to remove the unused kernels or keep the kernels and just delete the extra text from /boot/grub/grub.cfg 
i would go with the kernel removal but you are free to choose whatever you want 

here's a nice guide on kernel removals
[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

---

### Post by TeoBigusGeekus on 2011-08-28
These are the different entries for the various kernel versions that you have installed on your system.
It is generally advised to keep the latest 2 kernel versions: if something goes wrong with the latest kernel, you can always switch to the previous one.
If you want to delete older kernel images, open Synaptic Package manager and search for linux-image.
Keep the latest 2 and right click and select Completely remove for the older ones.
After you're done, open a terminal and give
```
sudo update-grub
```
to update your grub (the bios you mentioned isn't bios: it's "grub", ubuntu's bootloader) and you're finished.

---

### Post by 00ps on 2011-08-28
Ah that's why Google couldn't help me, I was searching for the wrong thing! My newbieness precedes me, calling a bootloader a bios, oh dear. 

Thank you!

---

### Post by realzippy on 2011-08-28
You not need to purge the older kernels,you can also
edit the grub menu to your likes with grub-customiser

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by bakegoodz on 2011-08-28
I like to delete the old kernels, more tidy. Ubuntu likes to recreate grub, so every kernel update it will read all the kernel files in /boot and put them (back) into grub.cfg

---

### Post by papibe on 2011-08-28
You can use synaptic to remove/uninstall old kernels. It would be a good idea to keep at least one old, though.

Check this [article ]("http://www.omgubuntu.co.uk/2011/07/kernel-entries-gone/")(video included) for the details on how to do it.

Regards.

---

