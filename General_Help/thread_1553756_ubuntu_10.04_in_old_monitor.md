---
title: "ubuntu 10.04 in old monitor"
date: 2010-08-15
forum: General Help
---

### Post by kishordgupta on 2010-08-15
i have very old monitor which could not support more than 800*600*16. 
so when i use winxp or win 7 i have to set enable vga mode. but  ubuntu 10,04 it was not possible.

after install ubuntu 10.04 , when gui cames monitor screen became distorted.
so i go grub menu press e and add vga=0314 beside "quite splash" but i got "VGA=0314 is deprecated. Use set GFX payload=[h][w][] using  the linux command instead." error and nothing happened.

then i go grub menu bu pressing crtl+c from boot option and then write command 
set gfxmode=800*600*16 but no error shown but nothing worked. also i write several command like set gfxplaymode=... etc. but nothing work.

i use ubuntu 9.04 without any troubles in this machine. so i need help.

also i can go terminal by shellmenu but its also distorted, so i cant edit grub file. i can only write in grub menu.

thanks

---

