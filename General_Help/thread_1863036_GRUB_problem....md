---
title: "GRUB problem..."
date: 2011-10-17
forum: General Help
---

### Post by PCman13 on 2011-10-17
Hi there,
 
I tried to install BURG, an graphical interface for GRUB, but during the installation, you have to choose which HDD you want to install BURG to. I went to my HDD using the arrow keys, but I think I had to press the space bar to select it, instead of enter. It skipped the installation completely, and now, when I boot my PC, I get a grub console :( 
 
Does anyone know how to boot Ubuntu from the GRUB console? If I manage to get into ubuntu, I think I'm able to fix it. I can't figure out how to use the boot command in the grub shell:
```

grub> boot
error: no loaded kernel.
 
 

```

---

### Post by haresear on 2011-10-18
This should work with grub2:

grub> set root=(hdX,Y)
grub> linux /vmlinuz root=/dev/sdZY ro
grub> initrd /initrd.img
grub> boot


X = drive bios # starting at 0 (e.g. hd0).
Y = partition # starting at 1.
Z = drive device id starting at 'a' (e.g. sda)

---

### Post by garvinrick4 on 2011-10-18
Or can:
[HOWTO: Purge and Reinstall Grub 2 from the Live CD - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1581099")

---

