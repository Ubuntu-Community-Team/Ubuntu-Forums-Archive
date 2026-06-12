---
title: "Question About Bootable ISO's"
date: 2010-07-30
forum: General Help
---

### Post by lateralus01 on 2010-07-30
I have a bootable usb stick with a Linux utility on it.  After poking around for a bit I figured out the boot order:

isolinux.bin  <--reads isolinux.cfg
loads the kernel: SA.1
loads initrd: SA.2

then depending on the options you select it boots one of two .iso files

I want this utility to netboot instead of booting with a usb stick; is there a way I can package isolinux.bin, isolinux.cfg, the kernel and initramfs, iso's and all the other files on the root of the usb stick into one iso that can be tftp'd to the host which would then boot something that would extract the iso to ramdisk and start booting so that isolinux would run as if all the files were locally stored on CD/usb stick?


Thanks,
Lateralus01

---

### Post by lateralus01 on 2010-07-31
bump

---

### Post by lateralus01 on 2010-08-01
anyone?

---

### Post by lateralus01 on 2010-08-02
Figured it out:

dd the usb stick to a file:

dd if=/dev/sdc1 of=./usb.dat

then load the image with memdisk:

label dellbios
    menu label Dell Poweredge r410 BIOS tool
    kernel memdisk
    append initrd=/dell/r410/usb.img harddisk noedd

---

