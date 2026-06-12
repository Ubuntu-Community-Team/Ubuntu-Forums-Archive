---
title: "Grub is gone but Ubuntu still there. I can only boot to Windows! Help!"
date: 2011-05-16
forum: General Help
---

### Post by BinRoot on 2011-05-16
edit: please delete post

---

### Post by alphacrucis2 on 2011-05-16
> **BinRoot said:**
> I ran the following from a live cd: 

```
sudo apt-get install lilo 
sudo lilo -M /dev/sda mbr
```[FONT=monospace]
So now I can successfully boot up Windows. But I want to boot Ubuntu now; however, the grub menu never shows up. Seems like my BIOS is bypassing it. 


Why would you expect to see a grub menu when you just overwrote the grub boot loader with lilo?

---

