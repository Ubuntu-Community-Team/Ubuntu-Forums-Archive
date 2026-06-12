---
title: "xmodmap to remap right arrow to right shift key"
date: 2009-10-13
forum: General Help
---

### Post by frazerr on 2009-10-13
hello,

My right arrow key on my keyboard is broken,
so I used .xmodmaprc to remap it to the right shift key

keycode  62 = Right NoSymbol Right NoSymbol Right

some issues:
I want it to stop also being a shift key,
and I can't hold it down to move right more than one place
and I cant use it with ctrl-shift-right to highlight words
and I cant use it with ctrl-shift-alt-right to move it to other desktops

any suggestions on how to make it work correctly?

---

### Post by frazerr on 2009-10-18
any one xmodmapped arrow keys before?

---

### Post by mike555 on 2009-10-18
try "xkeycaps"  I use it to make capslock a l.shift (with no lock).. it wont put a launcher in your menu , after install just type"  xkeycaps  "in terminal .

---

### Post by frazerr on 2009-10-19
I tried xkeycaps, and although it is **FUBARed** in respect to some keys on the eeepc

it gave me the idea to 
remove Shift   = 62

and then in the options it gave me the idea to search for auto-repeat
and I found to add    'xset r 62'     to one of my start up scripts 
( which  I put in /etc/rc.local - is that ok?)

[B]
so two problem solved:[/B]
I want it to stop also being a shift key,
and I can't hold it down to move right more than one place
[B]
two more to fix:[/B]
I cant use it with ctrl-shift-right to highlight words
and I cant use it with ctrl-shift-alt-right to move it to other desktops

any suggestions?

---

