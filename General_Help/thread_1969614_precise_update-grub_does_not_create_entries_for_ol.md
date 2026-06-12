---
title: "precise update-grub does not create entries for older Ubuntu installation"
date: 2012-04-30
forum: General Help
---

### Post by jamadagni on 2012-04-30
After doing a clean install of Precise, I find that update-grub does not create a GRUB entry for my older installation of Kubuntu viz Oneiric. On my system the layout is as follows:

sda1 Win-7-Root NTFS
sda2 Win-7-Data FAT
sda3 Linux-Swap
sda4 Extended
sda5 Precise-Boot EXT3
sda6 Precise-Root EXT4
sda7 Linux-Home EXT3
sda8 Linux-Home-Big EXT3
sda9 Oneiric EXT4

When running the update-grub script in Precise sure enough it says it has detected Oneiric but it does not output the appropriate grub.cfg entry:

```
$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Ubuntu 11.10 (11.10) on /dev/sda9
done
$
```

The contents of /etc/grub.d/ folder are unmodified from a pure Precise install. I have attached the output grub.cfg. Can anyone please help?

---

### Post by jamadagni on 2012-04-30
Well the problem was solved somewhat. Apparently if there is already a grub.cfg file in the boot directory of the other Ubuntu installation, the update-grub script reads that file and botches up in some way the creation of the actually needed grub.cfg file. After my renaming the other grub.cfg to grub.cfg.txt (or anything else) the update-grub script of Precise creates the correct grub.cfg entries to be able to boot the older Ubuntu installation.

---

### Post by bitinerant on 2012-05-04
Possibly related:  [https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/674841](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/674841)

---

