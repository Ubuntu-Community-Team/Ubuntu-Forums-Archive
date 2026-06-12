---
title: "Applying custom keyboard layout."
date: 2011-12-19
forum: General Help
---

### Post by Infil on 2011-12-19
Ubuntu  Applying custom keyboard layout.

Hello,

I'm using Ubuntu 11.10 64-bit and I'm using Unity (as default as it gets, I think).

I've modified the standard Norwegian keyboard layout ([FONT="Courier New"]/usr/share/X11/xkb/symbols/no[/FONT]). I used the "nodeadkeys" variant as a base and modifed which changes it does to the regular keyboard layout. I've attached the file (renamed to no.txt). The difference between my file and the one provided by 11.10 is lines 55 to 69, inclusive. Nothing else. What I am trying to achieve is that AltGr + R/T/F/G produce {/}/[/], respectively.

I have two problems:
**1.** How do I apply it, either temporarily or permanently? [FONT="Courier New"]setkkbmap no nodeadkeys[/FONT] at least seems to change to the nodeadkeys layout. Doing the following, however, does not work: [FONT="Courier New"]setkkbmap no bracesbrackets[/FONT]. Have I done something wrong? It appears to me that I've just modified the layout file entirely equivalently to the way the nodeadkeys layout does it.

**2.** How do I make it appear in the regular Gnome control panel? I've edited [FONT="Courier New"]base.lst[/FONT] and [FONT="Courier New"]base.xml[/FONT] correctly as far as I can see, but it won't appear even after reboot. Perhaps because there is something fundamentally wrong with my solution?

Thanks! :)

---

### Post by danpav2881 on 2011-12-21
Hi, you did only a really little mistake

You edited files base.lst and base.xml

In Ubuntu 11.10 it's not necessary. You have to edit evdev.xml and evdev.lst.

I worked on my own layout and now all it works :)))

If you want to know what I did take a look here:

[http://ubuntuforums.org/showthread.php?t=1894982](http://ubuntuforums.org/showthread.php?t=1894982)

I hope to be useful, have a good work :D :popcorn:

---

### Post by Infil on 2011-12-27
Thank you very much! Editing evdev.lst and evdev.xml worked! :D

---

