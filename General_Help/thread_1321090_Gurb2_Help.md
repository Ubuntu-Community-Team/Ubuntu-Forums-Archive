---
title: "Gurb2 Help"
date: 2009-11-09
forum: General Help
---

### Post by losgat on 2009-11-09
hi all

grub update does not configure my drives correctly and i need help......

drive setup 

UBU
/dev/sda1   *           1          61      489951   83  Linux
/dev/sda2              62       13192   105474757+   5  Extended
/dev/sda5              62        1034     7815591   82  Linux swap / Solaris
/dev/sda6            1035       13192    97659103+  83  Linux

WINBLOWS
/dev/sdb1   *           1        9728    78140128+   7  HPFS/NTFS

update-grub2 gives me the following output


Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done

:~# cat /boot/grub/device.map 
(hd0)    /dev/sda

with the old menu.lst everything worked fine after some simple drive mapping 

...................
map                (hd0) (hd1)
map                (hd1) (hd0)
.......................

how do i map, remap my drives in grub2??


Thanks

---

### Post by losgat on 2009-11-13
does anyone have an answer to to this???

---

### Post by ensign.dan on 2009-11-13
Try 
grub --device-map
update-grub
maybe this will help.

---

### Post by tommcd on 2009-11-13
If that does not work, you can try creating a custom entry for Windows in /etc/grub.d/ as per the grub2 tutorial in the Ubuntu wiki:
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)
There is an example for Windows in the sample grub.cfg file that is listed there. I had to create a custom entry for Slackware64. Using the advice in that tutorial worked perfectly.
Remember to run "sudo update-grub" after creating a custom entry in /etc/grub.d/.

---

