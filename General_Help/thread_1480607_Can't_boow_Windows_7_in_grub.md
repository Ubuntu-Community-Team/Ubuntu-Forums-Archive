---
title: "Can't boow Windows 7 in grub"
date: 2010-05-11
forum: General Help
---

### Post by ragum on 2010-05-11
I had Ubuntu 9.04 installed and after I updated I was unable to boot Windows 7 in the grub. The screen just stays blank when I click on it. Windows 7 is in my grub.cfg file.

menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 22dbaa7038e6dc50
    chainloader +1

Thanks in advance

---

