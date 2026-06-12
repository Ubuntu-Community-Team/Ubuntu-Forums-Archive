---
title: "ubuntu wont boot. just shows black screen"
date: 2010-06-03
forum: General Help
---

### Post by insanity99 on 2010-06-03
hey, last night i was really happy because i made a proper install on ubuntu, whereas previously i was on WUBI. everything seemed really fine i did the multimedia guide and installed some essential software. i even restarted a few times to be sure. but the next day it wont boot. it just shows a black screen. i have tried recovery mode, updated grub and chose to boot but it was in CLI mode so i forced shutdown cause i cant do anything there.

what can i do? i also tried the other kernels thats where listed.

thanks.

EDIT: if it helps i am on ATI graphics card. also it isn't a broken graphics card because it works fine on my live USB and so does windows.

---

### Post by dino99 on 2010-06-03
try to boot by editing (e) the boot line into grub menu, and removing "quiet splash" and/or adding nomodeset, then boot (x)
(if grub menu is hidden, at end of bios process, hold "shift" key down to see it)

if that work, edit /etc/default/grub to make change, then :

sudo update-grub

---

### Post by insanity99 on 2010-06-03
ah removing "quiet splash" worked, what a relife. so now i need to go to /etc/default/grub and make the change pernament?

---

### Post by dino99 on 2010-06-03
you can try removing only splash as i suspect it to be blamed

the next step is to modify /etc/default/grub and update it to have it permanent, on the other case you'll need to edit the boot line each time if you dont make it permanent, its your choice. This problem might be fixed soon i hope.

---

### Post by insanity99 on 2010-06-03
so should i remove this entire line?

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

or this line? GRUB_CMDLINE_LINUX=" vga=798 splash"

---

### Post by dino99 on 2010-06-03
> **insanity99 said:**
> so should i remove this entire line?[COLOR="Red"] no, only the word [COLOR="Blue"]splash[/COLOR][/COLOR]

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

or this line? GRUB_CMDLINE_LINUX=" vga=798 splash"

if you have [COLOR="Blue"]splash[/COLOR] on several lines, remove [COLOR="Blue"]splash[/COLOR] on all.

---

### Post by insanity99 on 2010-06-03
ok, it wont let me save changes. i guess i need to do it in terminal but i dont remember how.

---

### Post by dino99 on 2010-06-03
> **insanity99 said:**
> ok, it wont let me save changes. i guess i need to do it in terminal but i dont remember how.

into console: sudo gedit /etc/default/grub

---

### Post by philinux on 2010-06-03
> **dino99 said:**
> into console: sudo gedit /etc/default/grub

Make that gksudo gedit /etc/default/grub  ;)

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by insanity99 on 2010-06-03
ok this worked thanks guys. i will mark the thread as solved.

---

