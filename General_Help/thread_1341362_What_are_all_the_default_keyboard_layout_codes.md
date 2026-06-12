---
title: "What are all the default keyboard layout codes?"
date: 2009-11-29
forum: General Help
---

### Post by maxrocks_1 on 2009-11-29
Hello, I'm a user who needs to switch seamlessly between Russian and English keyboard layouts. I prefer the USA Alternate-International layout and the standard Russian layout. Usually I simply use the xkb GUI tool to accomplish this, but I just switched my system over to LXDE (it's a new system, 2.1GHz processor with 1GB of RAM, I just want to give LXDE a good try and another user, and on my older system with 500MB RAM and 1.6GHz it made everything REALLY noticeably faster), and there is no more Xkb tool. Therefore I am doing what I did before I discovered the GUI tool on xfce and having this script run at startup:

> #!/bin/sh
setxkbmap -option grp:alt_shift_toggle,grp_led:scroll us,ru

It works, but I would REALLY prefer to be using the USA Alternate-International layout instead of the standard US layout (it makes it easier to type accents in French/English). I would also like to have the toggle between layouts to be activated by just hitting the Windoze key (start key) as I did when using the Xkb GUI tool in xfce instead of having to hold down two keys (left Alt and Shift).

So does anyone know the layout code for USA Alternate-International, AND how I could make this activate every time I hit the Windoze key?

Thank you in advance for all the replies! (I hope I get some)

~Maxwell

---

### Post by maxrocks_1 on 2009-11-30
*Bump* I seriously need help here people.

---

### Post by maxrocks_1 on 2009-12-02
Bump again.

---

### Post by maxrocks_1 on 2009-12-06
Seriously people, a little help here?

---

### Post by andreylosev on 2010-10-21
NECROBump. I need help with this too.

---

### Post by ambeginnersearchinginfo on 2010-10-27
Did you try
 layout us_intl ?
Why don't you isntall and select also the french keyboard layout?
You can select more than two layouts.

---

### Post by ambeginnersearchinginfo on 2010-11-10
The language short cuts I found on the live cd at

usr/share/X11/xkb/symbols
.:)

---

