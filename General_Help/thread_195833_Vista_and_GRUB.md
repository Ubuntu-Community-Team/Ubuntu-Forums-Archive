---
title: "Vista and GRUB"
date: 2006-06-13
forum: General Help
---

### Post by seshomaru samma on 2006-06-13
Dear all
I'm running Dapper but wanted to try the new Vista beta 2. I resized Dapper a bit and installed Vista (it didn't detect my VGA card , it was a nightmare...). Anyway ,Windows over wrote over the MBR which left me Grub-less and consequently Ubuntu-less. Luckily I followed some excellent advice I got in Ubuntu's IRC channel – used the live CD chrooted to my system and ran 
```
grub
root (hd0,0)
setup (hd0)
```
anyway to make a long story short, I now have Ubuntu back , its just that Grub cannot see Vista. I know I need to add an entry to my grub/menu.lst but what should i write? Anybody has any experience with dualbooting Ubuntu/Vista?
here's my fdisk:
```

/dev/hda1               1        3824    30716248+  83  Linux
/dev/hda2            3825        3895      570307+  82  Linux swap / Solaris
/dev/hda3   *        3896        9726    46835712    7  HPFS/NTFS
```

---

### Post by zxee on 2006-06-13
In /boot/grub/menu.lst > title vista  ,2nd line, rootnoverify (hd0,2) ,last line,  chainloader +1  don't type in the line designators between the commas or the commas i.e each entry should have it's own seperate line (title, rootnoverify, chainloader) Hope that helps.

---

### Post by seshomaru samma on 2006-06-14
Thank you ,it worked

---

