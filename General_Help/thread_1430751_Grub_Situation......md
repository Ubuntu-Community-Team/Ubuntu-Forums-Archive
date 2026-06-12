---
title: "Grub Situation....."
date: 2010-03-15
forum: General Help
---

### Post by bigsmitty64 on 2010-03-15
All of a sudden, when grub2 loads I see all my drives available, but cannot boot into win7. 
Here is the readout from update-grub:

```
Generating grub.cfg ...
Found Debian background: Ubuntu_Linux.png
Found linux image: /boot/vmlinuz-2.6.31-20-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-20-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-19-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-19-generic-pae
Found Mac OS X on /dev/sdb2
Found Windows 7 (loader) on /dev/sdd1
grub-probe: error: Cannot find a GRUB drive for /dev/sdd1.  Check your device.map.

```

---

### Post by dcstar on 2010-03-15
> **bigsmitty64 said:**
> All of a sudden, when grub2 loads I see all my drives available, but cannot boot into win7. 
Here is the readout from update-grub:

```
Generating grub.cfg ...
Found Debian background: Ubuntu_Linux.png
Found linux image: /boot/vmlinuz-2.6.31-20-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-20-generic-pae
Found linux image: /boot/vmlinuz-2.6.31-19-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-19-generic-pae
Found Mac OS X on /dev/sdb2
Found Windows 7 (loader) on /dev/sdd1
grub-probe: error: Cannot find a GRUB drive for /dev/sdd1.  Check your **device.map**.

```

/boot/grub/device.map

---

### Post by bigsmitty64 on 2010-03-16
So,

boot/grub/device.map says 

(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc

what do I add in here?

---

### Post by bigsmitty64 on 2010-03-16
:)

---

### Post by bigsmitty64 on 2010-03-17
Still not straightened out yet. Anyone  at all?

---

### Post by Herman on 2010-03-17
Try running 'sudo grub-mkdevice.map' and then run 'sudo grub-mkconfig -o /boot/grub/grub.cfg and see what happens.
```
sudo grub-mkdevicemap
```
```
sudo grub-mkconfig -o /boot /grub/grub.cfg
```Maybe those two commands will fix your GRUB2 automatically. :D

---

### Post by bigsmitty64 on 2010-03-17
Thank you Herman, that did the trick!

---

### Post by Herman on 2010-03-18
8-) Cool!

---

