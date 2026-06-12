---
title: "menu.lst not found, i can't change the order of startup os"
date: 2011-09-17
forum: General Help
---

### Post by gerdy.debusschere on 2011-09-17
Help.
When i start my computer now i can chose normally witch os must start.
I must select with the arrow keys but they don’t work. I’m using a usb  keyboard and think this is the reason i can’ t use the keyboard when  starting up.
I can’t also edit menu.lst . It isn’t found when i use search.
Anyone can help me?
Thx

---

### Post by TeoBigusGeekus on 2011-09-17
Menu.lst was the file for grub legacy.
Nowadays, ubuntu uses grub2 and the file you want to change is /etc/default/grub. So...
```
gksu gedit /etc/default/grub
```
Change the GRUB_DEFAULT=0 value to whatever suits you.

By the way, look into your bios to enable usb legacy support and see if it does anything for your keyboard.

---

