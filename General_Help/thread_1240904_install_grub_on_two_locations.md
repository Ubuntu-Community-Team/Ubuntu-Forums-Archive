---
title: "install grub on two locations"
date: 2009-08-15
forum: General Help
---

### Post by zelhar on 2009-08-15
I think I have grub installed both on (had0) and on (hd0,3) which is my ubuntu's root  partition. As it seems now i can boot my system and everything works fine. But what I would like to know is if I install a different bootloader on the MBR would I be able to chainload into my current grub ?

---

### Post by blueridgedog on 2009-08-15
Grub is more than likely installed in the master boot record of hd0 and looks to hd3 for it's boot files in the event that you elect to load Ubuntu.  If you install another bootloader to hd0, grub will be overwritten and it will be up to the new bootloader to load your Ubuntu installation.  

You are welcome to experiment as reinstalling grub in the event of a goof is easy IF you have the CD.

---

### Post by zelhar on 2009-08-15
If I need to reinstall grub to my ubuntu partition, is that the correct command:
> 
"root (hd0,3)" 
"setup (hd0,3)"

will such command setup a new menu which is automatically updated in case of a new kernel is installed ?

---

### Post by blueridgedog on 2009-08-15
If what you posted about your drive setup is accurate, then:

```
root (hd0,3)
setup (hd0)
```

For the setup command, keep in mind that you setup drives, not partitions, hence the reference only to the drive.

It should update when new kernels are installed.

---

### Post by zelhar on 2009-08-16
I think setup (hd0,3) installs grub in the ubuntu partition, so I can then install another boot manager in the MBR.

---

### Post by blueridgedog on 2009-08-16
It is worth a try...I have never used it that way.  You can always re-install if it fails to work as expected.

---

