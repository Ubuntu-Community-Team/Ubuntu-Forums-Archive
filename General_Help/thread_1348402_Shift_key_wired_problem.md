---
title: "Shift key wired problem"
date: 2009-12-07
forum: General Help
---

### Post by ristepan on 2009-12-07
Hi, to every one!
This is my first post and first problem that driving me crazy, from when I am on Ubuntu, about one month ago.
**Shift key this morning just stop functioning**, properly.
when i hold shift key cursor stops blinking and can't write upper cases
and $%# and similar signs.
This thing happens in all applications except in Opera address bar when drop down history i on :}
Problem occur in [COLOR="Red"]Virtual box[/COLOR] but in [COLOR="#ff0000"]vmWare player[/COLOR] is OK,   
In console (Ctrl+Alt+F1) Shift key is OK

and in [COLOR="DarkRed"]Gnome safe mode[/COLOR] session is OK ?!?

P.S.
may be something stupid but I'm pretty new on Ubuntu

---

### Post by hal10000 on 2009-12-07
Maybe you accidently used the shift lock key, just hit it again and try out wether yout shift key is working now.

---

### Post by ristepan on 2009-12-07
nop, 
 I&#8217;ve been tried everything, rebooted many times, 
started in gnome safe mode shift is OK. 
back in Gnome normal mode and shift again does not work

Just noticed another craziness in password dialog, for synaptic, shift is working correctly, I have some upper cases in root password

---

### Post by ristepan on 2009-12-07
Yeep SOLVED, I've managed to locate the problem, problem is in Compiz, after some install and uninstall componets,(KDE, Compiz  fuzion icon, CompizConfig menager and bunch of other stuff). Uncheking the Preferences->CompizConfig settings manager->Commands check box solved te problem ?!?
What are that commands I do not now and I do not want to now :)

---

### Post by Stam_Black on 2010-11-16
I think that CompizConfig might be a partial solution to the problem...
It could be that it is actually the Fn-key that is stuck...try turning numlock off.

---

