---
title: "I need info about my computer!!"
date: 2006-06-28
forum: General Help
---

### Post by morbid_bean on 2006-06-28
How do i find out basic info about my computer....such as finding out my processor, the amount of ram i have etc...

---

### Post by vigleik on 2006-06-28
For the processor, "$less /proc/cpuinfo". (But note that it gives the current clockspeed, not the maximal, in case you have some kind of powersave.) For general HW info, there are several programs. For example, "#lspci -v" or "#lshw". You could also install hwinfo, which gives a similar list. (Here # means run as root, or put sudo before the command.)

Vigleik

---

### Post by glotz on 2006-06-28
.

---

### Post by johnc4510 on 2006-06-28
Try this command:
sudo lshw

---

### Post by Marcos.Rufino on 2006-06-28
[QUOTE=johnc4510]Try this command:
sudo lshw[/QUOTE]

Very cool!

---

### Post by thasheep on 2006-06-28
[QUOTE=johnc4510]Try this command:
sudo lshw[/QUOTE]
That's very useful (and 'sudo lshw | less'). For similar information in a graphical view in gnome (ubuntu), go System>Administration>Device Manager.
Another very useful command line tool is lspci. In order of least information to most:
```
lspci
lspci -v | less
lspci -vv |less
sudo lspci -vvx | less
```Chances are lspci by itself will tell you more than enough (about pci devices at least).

---

