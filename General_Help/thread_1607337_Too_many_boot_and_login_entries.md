---
title: "Too many boot and login entries?"
date: 2010-10-27
forum: General Help
---

### Post by Bitech on 2010-10-27
I've been using (K)Ubuntu for about a month now, and I can't seem to ignore the number of boot entries and login entries I get everytime I log in.

I'm only dual booting Windows 7 and (K)ubuntu but my grub shows:

Found linux image: /boot/vmlinuz-2.6.35-23-generic
Found initrd image: /boot/initrd.img-2.6.35-23-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2

I currently use version .35-22. The -23 version was an attempt to fix the notorious screen brightness bug through this thread 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1603697](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1603697)
but all I end up in is a black screen, starting from the login. I'm not sure why the earlier linux image is still sitting there, and my computer came preloaded with windows 7 so i dont know why vista is even there.

And then on a normal login session I only choose between KDE and "Ubuntu Desktop Edition", but there's 8 other entries:

Default
"User-Defined Session"
Recovery Console
Ubuntu (Safe Mode)
3 copies of "guest-restricted"
and FailSafe

I can understand Recovery console and Safe mode, Failsafe seems like a troubleshooting session as well but I dont know what it is, and I dont know the purpose of the other entries.

What's the purpose of each of these entries and how can I delete the useless ones? Thanks

---

### Post by TeoBigusGeekus on 2010-10-27
All these "versions" are linux kernels. Whenever you install a new kernel ubuntu doesn't delete the older ones for safety reasons.
To get rid of some of them, open synaptic package manager, search for linux image and delete the ones you don't want; it is generally advised to keep at least 2 kernels on your system, one to operate with and an older one as a failsafe retreat in case something goes wrong with the newer one.
When you're done uninstalling the images you don't want, run
```
sudo update grub
```

---

### Post by Mark Phelps on 2010-10-27
> **Bitech said:**
> ... and my computer came preloaded with windows 7 so i dont know why vista is even there.

Vista is probably NOT there.  With default Win7 installs, the boot loader files are installed to one partition, the OS and remaining files to a second partition.

Since the boot loader is essentially the same with both Vista and Win7, in these cases, it's not unusual for the OS prober to think the first partition has Vista on it.  Since the Win7 OS files are on the second partition, it KNOWS that contains Win7.

It's merely a cosmetic bug. And, in some cases, GRUB actually gets the order of the partitions reversed.  So, while it would make sense to choose the Vista entry over the Win7 (because THAT's where the boot loader files are kept), in some cases, it's better to choose the second entry, not the first.

---

