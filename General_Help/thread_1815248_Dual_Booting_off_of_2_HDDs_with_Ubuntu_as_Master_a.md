---
title: "Dual Booting off of 2 HDDs with Ubuntu as Master and Windows Vista as Slave"
date: 2011-07-30
forum: General Help
---

### Post by MartinFernando1993 on 2011-07-30
Hey Forum:

I recently installed a second hard drive on my Ubuntu Machine with Windows Vista pre-installed. When I boot my machine, by default, it loads Ubuntu 10.10 and not the Grub Boot manager. Days later I updated grub and this is what I got in the terminal
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-30-generic
Found initrd image: /boot/initrd.img-2.6.35-30-generic
Found linux image: /boot/vmlinuz-2.6.35-28-generic
Found initrd image: /boot/initrd.img-2.6.35-28-generic
Found linux image: /boot/vmlinuz-2.6.35-27-generic
Found initrd image: /boot/initrd.img-2.6.35-27-generic
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sdb1
done

```

I'm wondering why Vista has "loader" in parentheses. When I try to boot it as is, Vista won't load. Now, I don't want to install Windows first because I don't want to, but I've heard some have been successful in making Ubuntu the master OS and Windows the Slave.

I'd appreciate all suggestions regarding this issue

Thanks
Martin

---

### Post by DigitalAlcatraz on 2011-07-31
Windows Vista has loader in the parenthesis as grub doesn't boot in to Vista directly, but it loads whe windows boot loader which loads vista. Do you see the Windows Vista option in the grub menu, if you see the grub menu at all? have you set your HDD containing GRUB as the boot device in your BIOS? Ubuntu can be the master OS even if it is installed after windows.

---

