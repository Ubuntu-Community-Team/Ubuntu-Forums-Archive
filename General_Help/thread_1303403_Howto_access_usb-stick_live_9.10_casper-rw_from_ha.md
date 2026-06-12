---
title: "Howto access usb-stick live 9.10 casper-rw from harddisk 8.04 ?"
date: 2009-10-28
forum: General Help
---

### Post by Frank Zapppa on 2009-10-28
Stick lost grub, and now I need to save staff with 8.04 which locates in hard disk..
Howto access usb-stick live 9.10 casper-rw from harddisk 8.04 ?

I tried: sudo mkdir /media/casper
           sudo mount -o loop (/dev/sdb/)casper-rw /media/casper

but it says only that casper-rw is not a directory.

Anyone pro knows a solution ?

T: Frank Zappa 8)

---

### Post by The Cog on 2009-10-28
When you are mounting a file looped, you need to specify the file rather than the device. I think casper-rw is probably a file in /media/disk/casper-rw or /media/ubuntu/casper-rw, not in /dev at all. So try:
```
sudo mount -o loop /media/ubuntu/casper-rw /media/casper
``` but of course replace "ubuntu" with whatever the stick shows up as.

---

