---
title: "limit number of kernels at grub"
date: 2012-06-28
forum: General Help
---

### Post by bryncoles on 2012-06-28
Greetings fellows!

I was wondering if there was a simple way of limiting the number of Kernels shown by Grub at boot?  I have Googled, but I do not understand what I have read from that search!

I currently have Xubuntu 12.04 installed, and I see only 1 Kernel at boot.   I'd like an option of the last 2 kernels.  

Is there an easy, idiot proof way of fixing this?

Cheers guys!

---

### Post by drs305 on 2012-06-28
By default, the latest version of GRUB 2 will display the latest kernel on the main menu and place any older kernels installed on your system in the "Previous Linux versions" submenu.

If you don't have such a subfolder:
1. Did you upgrade from an earlier release with an older Grub version? Do you have Grub 1.99
```
grub-install -v
```
2. Do you have other kernels installed on your system?
```
ls /boot | grep vmlinuz
```
3. Have you tried  updating the Grub menu?
```
sudo update-grub
```

Here is a link about *removing* older kernels, which would also remove them from the menu:
[http://ubuntuforums.org/showthread.php?t=1587462]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by bryncoles on 2012-06-28
Hi drs305!  Nice to see a swift response!

To answer your questions in order:

I think this was a fresh install of 12.04, as I jumped ship from Ubuntu with this release.  However, it seems I'm running Grub 1.99:

```
grub-install -v
grub-install (GRUB) 1.99-21ubuntu3.1
```

I do have other Kernels installed though:

```
ls /boot | grep vmlinuz
vmlinuz-3.0.0-19-generic
vmlinuz-3.2.0-24-generic
vmlinuz-3.2.0-25-generic
```

And I have updated Grub:

```
sudo update-grub
[sudo] password for user: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-19-generic
Found initrd image: /boot/initrd.img-3.0.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
done
```

Yet I still just have the options of booting into the current grub, the recovery mode or the memtest.  No old Kernels!  Boo!

---

### Post by drs305 on 2012-06-28
The best course of action now is probably to install and run Boot Repair and post the contents or link to the results of the boot info script. 

That will allow us to see how your system is set up.

A link to Boot Repair is in my signature line.

---

### Post by bryncoles on 2012-07-03
-_- Red face.  I found all the old kernels... turns out that they're hidden in the 'previous releases' sub menu, which turns out to be a menu, not a heading!  So, this was a case of PEBCAK!

Thanks for the help though drs305, I still learned some useful knowledge!

---

