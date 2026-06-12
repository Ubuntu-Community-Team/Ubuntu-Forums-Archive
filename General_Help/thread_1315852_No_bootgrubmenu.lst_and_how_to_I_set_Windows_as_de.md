---
title: "No /boot/grub/menu.lst and how to I set Windows as default?"
date: 2009-11-05
forum: General Help
---

### Post by donTommazo on 2009-11-05
Hi,

I have just installed Ubuntu 9.10 on my wife's laptop. Since she is so excited about Windows 7, she wants it to be the default boot option in GRUB. 

But I can't find /boot/grub/menu.lst which feels quite weired. Have the grub setting files been changed since earlier releases of Ubuntu? 

How to I make Windows to be the default option in grub!?

Thanks in advance
/ Tomas

Ps. Attaching the output from > ls -la /boot/grub/

---

### Post by Giblet5 on 2009-11-05
```
sudo gedit /etc/default/grub
```

Find GRUB_DEFAULT near the top.

Change GRUB_DEFAULT=0

to

GRUB_DEFAULT=saved

Then run these two commands: ```
sudo update-grub
sudo grub-install `grep hd0 /boot/grub/device.map | tail -1 | awk '{ print $2 }'`
```

(copy/paste those...)

Now, you will default boot whatever you booted last time.

You can force it to boot Windows, but that will break the next time a linux kernel is released. The numbering scheme is pretty easy:
0
1
2
3
...

---

