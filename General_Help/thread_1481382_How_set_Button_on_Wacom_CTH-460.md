---
title: "How set Button on Wacom CTH-460"
date: 2010-05-12
forum: General Help
---

### Post by vdr60 on 2010-05-12
I just upgraded to Lucid and reinstalled Wacom driver for my CTH-460 Bamboo, but I cannot set Button1 to PagUp.....

I tried these cmd:

1) xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button1 "key core pgup"
But I receive msg: Invalid key 'CORE'
2) xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button1 "core key pgup"  (swapping core and key keywords)
But I receive msg: Invalid key 'pgup'

I tested also using pagup instead of pgup with the same results; so I used
xsetwacom list mod
in order to see which modifiers could be used, but unlikely i got the msg:
unknown argument to list

I am very lost, anyone can help me?

UPDATE:
If I send 
xsetwacom set "Wacom BambooFun 2FG 4x5 Finger pad" Button1 "CORE KEY ALT F2"
all works fine! I'm lost.

---

### Post by Favux on 2010-05-12
Hi vdr60,

The xsetwacom command page on the LWP's shows it both ways.  But the xsetwacom commands were rewritten for xf86-input-wacom.  I've seen 'core key' work in Lucid and your error messages seem to support that order.  Have you tried Pageup?  Also just enter xsetwacom in a terminal and see the options.  Maybe it's now 'xsetwacom mod list' for example?

---

### Post by vdr60 on 2010-05-16
Tested "xsetwacom mod list" but nothing as response.... 
I also thing that "core key" now is the rigth syntax, but I found nothing about modifier to be used (obviously I'm interested in PagUp and PagDn"

---

