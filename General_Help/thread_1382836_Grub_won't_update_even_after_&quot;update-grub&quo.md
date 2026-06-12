---
title: "Grub won't update even after &quot;update-grub&quot;"
date: 2010-01-16
forum: General Help
---

### Post by Mayur on 2010-01-16
Ok so I'm trying to edit my Grub menu by removing the older kernel after I ran updates as well as make my Windows 7 install first on the list.

I ran...
```
sudo gedit /boot/grub/menu.lst
```
and edited it accordingly.

After that I ran...
```
sudo update-grub
```

I restarted and see no changes on my grub menu.  Any help?  Running 1.97 beta4 if it makes a difference.

Oh and btw I am a complete n00b with linux.

---

### Post by Mayur on 2010-01-17
It's all good, I figured it out on my own.  Had to re-install grub.

---

