---
title: "Intel Corporation Mobile GM965/GL960 and compiz"
date: 2011-06-29
forum: General Help
---

### Post by mahermali on 2011-06-29
Hi all
I have a problem with compiz and this card, after few weeks suddenly it doesn't work with ubuntu, I always had troubles with this kind of cards, I was always able to solve it by this forum but this time I gave up.

The driver for GM965/GL960 is working perfectly but the compiz effects although they are enabled they are not applied to the desktop environment.

The compiz-check output is:

```
Gathering information about your system...

 Distribution:          Ubuntu 11.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
 Driver in use:         fbdev
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems..../compiz-check_0-4-6: line 491: [: 10505: binary operator expected
           [ OK ]

```also the Ubuntu version is:11.4

the compiz --replace gave errors, I can't capture it because the gui becomes unresponsive.
Thanks

---

### Post by claracc on 2011-06-30
I have VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) in my hp compaq 6720s laptop. I have also had problems with compiz. I couldn't use special effects since system freezes; I tried to use normal effects but there were glitches in the screen (not working properly) and the cpu load was high.

So I decided to use metacity instead of compiz, of course with no visual effects. However you can enable compositing with metacity to have a dock but without visual effects. My ubuntu is 10.04.

---

### Post by mahermali on 2011-06-30
Hi
I had compiz working perfectly with this kind of controllers, and the performance was amazing, so we can run it but we need to know the problem.
Thanks

---

