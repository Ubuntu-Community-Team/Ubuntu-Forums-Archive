---
title: "Create Keyboard Layout"
date: 2010-02-08
forum: General Help
---

### Post by jesuisbenjamin on 2010-02-08
Hello there,

According to [this article]("http://www.linux.com/archive/feature/113715"), one could create a custom keyboard layout.
While i look in the /ect/x11/xkb/ repertory i find a base.xml file only, no keyboard layouts as the article suggests.

Where can i find my keyboard layouts so i can edit them?

Thanks for helping.
B.

---

### Post by jesuisbenjamin on 2010-02-09
Anyone?

---

### Post by rnerwein on 2010-02-09
hi
first run in a terminal: [COLOR=Red]xev[/COLOR] print contents of X events (keycode etc.) to see the keycodes of your keyboard.
run: [COLOR=Red]xmodmap -pke[/COLOR] > my_layout.txt  
you can modify this file ( it's plain ascii ) to your behavior.
then run:[COLOR=Lime] xmodmap my_layout.txt[/COLOR]
is true for the whole session.
see also: man xmodmap, man xev

ciao

---

### Post by tom7 on 2010-02-25
In 9.10 you can find it in /usr/share/X11/xkb/symbols.

---

