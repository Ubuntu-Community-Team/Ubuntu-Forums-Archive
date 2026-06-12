---
title: "GRUB2 overwritten?"
date: 2010-09-11
forum: General Help
---

### Post by greenleaf9 on 2010-09-11
I'm using Truecrypt to encrypt my Windows 7 OS. I also have unencrypted Ubuntu 10.04 installed on /dev/sda6 on the same hard drive. Since Truecrypt bootloader must be installed in MBR, I have GRUB2 installed on /dev/sda6, so I can use TC bootloader to load GRUB2.
When I first  install GRUB2 on /dev/sda6, I can use TC bootloader to load Ubuntu. But, if I boot into Windows via TC bootloader, and then later try to boot into Ubuntu, I get the message "no bootable partition found". I have to reinstall GRUB2 onto /dev/sda6, every time after I use windows in order to be able to boot into Ubuntu. It seems that starting Windows somehow overwrites GRUB2. Is there a fix for this?

---

### Post by Lukas666 on 2010-09-12
For more complex setups I use this:

1. Windows bootlaoder as the main bootloader
2. Once it passes grub kicks in with its default selection screen.

Please read more here:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

and EasyBCD is a great piece of Software for Windows.

---

