---
title: "install backtrack on usb hard drive"
date: 2010-08-19
forum: General Help
---

### Post by spiky001 on 2010-08-19
Ok here is my setup I have win xp dual boot with Ubuntu Karmic, on hard drive I now want to install Bt4 on usb hard drive, will i just be able to install as normal then reinstall grub afterwards, also will the machine still work ok if usb drive is not attached on some occasions

My machine dos,nt  allow booting from usb, ( i,e install from usb drive )

---

### Post by spiky001 on 2010-08-20
Ok I have loaded backtrack on hard drive in pc. Now I want to put the drive in a usb caddy then refit the old ubuntu drive in machine,  I now need to boot the usb drive, Am I correct in thinking I need to chainload "sdb1 where boot is installed"  to grub if so do I edit grub cfg?

---

### Post by spiky001 on 2010-08-21
Having googled all day about problem went ahead installed on usb drive ran command
```
sudo update-grub2
```

got a reply
[PHP]Generating grub.cfg ...
Found Grub background: Gosalia.png
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Ubuntu 8.10 (8.10) on /dev/sdb1
grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

grub-probe: error: Cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

done
[/PHP]
any ideas please

---

### Post by spiky001 on 2010-08-21
Ok I solved this hope it helps others I edited the boot/grub/devicemap  by adding (hd1)  /dev/sdb then  ```
sudo update-grub2
```

---

