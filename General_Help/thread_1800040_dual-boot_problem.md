---
title: "dual-boot problem"
date: 2011-07-08
forum: General Help
---

### Post by TuxTorvalds on 2011-07-08
I deleted every trace of Linux Mint, I used Mint4Win to install Linux Mint, I know it's based off Wubi, I'm not an idiot... Linux Mint is still in the start-up...
 
 
HEEEEEEEEEEELLLLLLLLLPPPPPP!

---

### Post by User-007 on 2011-07-08
You mean that after purging Mint partitions the bootloader still exists?

Assuming you have installed the bootloader (grub) on MBR, have a look for a command

```
Bootrec.exe /FixMbr
``` 

You can google the instructions, I can't give the exact instructions since I don't know which Windows version you have. If Windows 7, here's one link:

[http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

Hope this helps,

User JB

---

### Post by Elfy on 2011-07-08
Thread closed. Please do not post duplicates, it dilutes community effort.

---

