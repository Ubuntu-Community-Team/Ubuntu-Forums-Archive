---
title: "grub into flashdrive?"
date: 2009-12-30
forum: General Help
---

### Post by gregwm on 2009-12-30
i have here a usb flash drive with Xubuntu 8.04.1 Hardy installed on it,
i'm not sure either via unetbootin or wubi.  i want to boot into it, from
this here thinkpad that has no usb bios support.  can anyone share with me
a suitable incantation that can be included in the grub.conf on my hd to
boot this little beast?  either syslinux.cfg or isolinux/isolinux.cfg
(both pasted below) probably contain suitable clues, but i might need a
bit more magic..?
tia,
gregwm

isolinux/isolinux.cfg:
 DEFAULT /casper/vmlinuz
 GFXBOOT bootlogo
 APPEND  file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
 LABEL live
  menu label ^Try Xubuntu without any change to your computer
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/xubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
 LABEL live-install
  menu label ^Install Xubuntu
  kernel /casper/vmlinuz
  append  file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.gz quiet splash --
 LABEL check
  menu label ^Check CD for defects
  kernel /casper/vmlinuz
  append  boot=casper integrity-check initrd=/casper/initrd.gz quiet splash --
 LABEL memtest
  menu label Test ^memory
  kernel /install/mt86plus
  append -
 LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
 DISPLAY isolinux.txt
 TIMEOUT 300
 PROMPT 1
 F1 f1.txt
 F2 f2.txt
 F3 f3.txt
 F4 f4.txt
 F5 f5.txt
 F6 f6.txt
 F7 f7.txt
 F8 f8.txt
 F9 f9.txt
 F0 f10.txt

syslinux.cfg:
 default vesamenu.c32
 prompt 0
 menu title UNetbootin
 timeout 100

 label unetbootindefault
 menu label Default
 kernel /ubnkern
 append initrd=/ubninit file=/cdrom/preseed/xubuntu.seed boot=casper quiet splash --

 label ubnentry0
 menu label ^Try Xubuntu without any change to your computer
 kernel /casper/vmlinuz
 append initrd=/casper/initrd.gz file=/cdrom/preseed/xubuntu.seed boot=casper  quiet splash --

 label ubnentry1
 menu label ^Install Xubuntu
 kernel /casper/vmlinuz
 append initrd=/casper/initrd.gz file=/cdrom/preseed/xubuntu.seed boot=casper only-ubiquity  quiet splash --

 label ubnentry2
 menu label ^Check CD for defects
 kernel /casper/vmlinuz
 append initrd=/casper/initrd.gz boot=casper integrity-check  quiet splash --

 label ubnentry3
 menu label Test ^memory
 kernel /install/mt86plus
 append initrd=/ubninit -

 label ubnentry4
 menu label ^Boot from first hard disk
 kernel /ubnkern
 append initrd=/ubninit -

 label ubnentry5
 menu label oem=OEM install (for manufacturers)
 kernel /ubnkern
 append initrd=/ubninit oem=oem-config/enable=true

---

