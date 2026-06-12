---
title: "Boot hangs without external hard drive"
date: 2011-06-20
forum: General Help
---

### Post by Aelos on 2011-06-20
Dual booted Windows 7 and Natty Narwhal, the Ubuntu boot hangs if external hard drives aren't present upon boot. Both OS's are loaded onto the internal drive.

---

### Post by drs305 on 2011-06-20
Most likely Grub2 is installed on the external drive. You can install it on the internal drive by mounting the Ubuntu partition and installing G2 while using the LiveCD:
```

sudo mount /dev/sdXY /mnt
sudo grub-install --root-directory=/mnt /dev/sdX
```
Change X to the internal drive (a,b,c, etc)
Change Y to the internal drive partition with Ubuntu (1,5, etc)
Do not use the Y value in the second command.
Make sure the computer's BIOS boots to the internal drive first.

If this doesn't work, click the "BIS" link in my signature line, run the Boot Info Script and post the contents of RESULTS.txt.

---

