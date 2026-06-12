---
title: "how add menu item in text.cfg?"
date: 2010-01-02
forum: General Help
---

### Post by sububtu on 2010-01-02
IM using Ubuntu 9.10 running from USB,

My current text.cfg --->

default live
label live
  menu label ^Run Ubuntu from this USB
  kernel /casper/vmlinuz
  append  locale=us_us bootkbd=us console-setup/layoutcode=en_US console-setup/variantcode=nodeadkeys noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz splash --

label live-install
  menu label ^Install Ubuntu on a Hard Disk
  kernel /casper/vmlinuz
  append  locale=us_us bootkbd=us console-setup/layoutcode=en_US console-setup/variantcode=nodeadkeys noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz splash --

label check
  menu label ^Check this USB for defects
  kernel /casper/vmlinuz
  append  locale=us_us bootkbd=us console-setup/layoutcode=en_US console-setup/variantcode=nodeadkeys noprompt boot=casper integrity-check initrd=/casper/initrd.lz splash --

label memtest
  menu label Test ^memory
  kernel /install/mt86plus
splash --
__________________________________________________________________________________

what i need is to add another boot options ,im familiar with the menu.lst written below


timeout 60 
default 0 
 
title Boot from Hard Drive 
rootnoverify (hd0,0) 
chainloader (hd0,0)+1 
 
title -------------------- 
root 
 
title Start Hiren's BootCD 
find --set-root /HBCD/boot.gz 
kernel /HBCD/memdisk 
initrd /HBCD/boot.gz 
 
title Mini Windows Xp 
find --set-root /HBCD/XPLOADER.BIN 
chainloader /HBCD/XPLOADER.BIN

i tried to add these lines in the test.cfg , but its not working.
i do hav these folders and files with in the disk,
please help me... thanks in advance..

---

### Post by dandnsmith on 2010-01-02
I think that you have a syslinux boot menu system there for the USB stick.

Perhaps searching for syslinux help on menus might get you somewhere - certainly the grub menu stuff you have isn't suited.

I confess that I've not yet had success with changing the syslinux boot actions.

---

