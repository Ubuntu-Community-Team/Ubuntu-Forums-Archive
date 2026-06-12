---
title: "CTRL-ALT-F7 fails to return me to X11"
date: 2010-08-13
forum: General Help
---

### Post by afrodeity on 2010-08-13
This is a problem which has been plaguing me ever since the upgrade from Karmic to Lucid.

I used to be able to log into any one of the seven TTYs.

CTRL-ALT F1-six all work fine. Problem is if I log into one I can't get back to the GUI.

Immediately after the upgrade, I was told by some people that this was deprecated along with startx and I should use sudo gdm service start  instead.

This doesn't work for me If I have to open a terminal when a nasty game freezes and I have to kill it from a terminal.

---

### Post by earthpigg on 2010-08-13
hi,

unfortunately, i cannot replicate your problem. i can log into a different tty, then press ctrl+alt+f7 to get back to the one with gnome running. either with or without typing 'exit' to log off on the tty.

i have a fairly standard ubuntu 10.04 install. do you have any insight about what could be different between our two setups?

the only thing i can see that seperates us, from your post, is that you upgraded from 9.10 to 10.04 whereas i did a fresh install.

---

### Post by wojox on 2010-08-13
Try CTRL+ALT+F8

I had to use that a few times before for some strange reason.

---

### Post by afrodeity on 2010-08-13
Hi earthpigg, at least you can confirm its not some new feature or something which is deprecated?

---

### Post by AlphaLexman on 2010-08-13
> **wojox said:**
> Try CTRL+ALT+F8

I had to use that a few times before for some strange reason.
Or even try CTRL + ALT + F9

---

### Post by afrodeity on 2010-08-13
Tried them all, but no go. Maybe I need a new keyboard?

---

### Post by wojox on 2010-08-13
> **afrodeity said:**
> Tried them all, but no go. Maybe I need a new keyboard?

Maybe. That's sort of strange it will let you switch but not return.

If I press Alt+F7 in Firefox, my cursor turns to a hand to move the screen around. Maybe it just your F7 key. Try it out.

---

### Post by earthpigg on 2010-08-13
> **afrodeity said:**
> Hi earthpigg, at least you can confirm its not some new feature or something which is deprecated?

i can only confirm that i've never seen the behavior you describe on either my netbook or my desktop, both running 10.04. apparently, no one in this thread has seen what you describe either.

try a different keyboard?

---

### Post by AlphaLexman on 2010-08-13
Please post the output of:
```
who
```
from a terminal

---

### Post by afrodeity on 2010-08-14
```

who
afrodeity tty7         2010-08-14 11:19 (:0)
afrodeity pts/2        2010-08-14 11:19 (:0.0)
afrodeity pts/1        2010-08-14 11:27 (:0.0)

```

---

### Post by carlturney on 2010-11-19
I too have the same problem: can not return to the GUI from tty1...6 using Ctrl-Alt-F7.

Never had a problem with Fedora Core 5, or Ubuntu 8.04, but do now with Ubuntu 10.4.1

Even worse, whenever I try to navigate away from tty1 using Ctrl-Alt-Fx my system locks up and I have to hit the reset button on my system.

Mine is a clean install of Lucid on a dual-boot disk with Win XP and GRUB defaulting to Ubuntu.  I've got an old standard graphics card and have done nothing graphics-wise except drop my GUI screen resolution down to 1024x768 from a somewhat higher default resolution upon install.  Ample RAM and swap & disk space, Gigabyte GA-G1975X motherboard, Dual Core Pentium D.

Hope you can give some advice soon.

Carl, New Zealand

---

### Post by svaens on 2010-12-15
I have the same problem now, with 10.10.

I can escape X ok using F2, 
but in trying to get back with F7, 
all I get is a screen which has messed-up console like monoscript all over it ..... 
pressing F2 again does bring me back to console,  but no matter how many times I try, no luck with F7.

---

### Post by earthpigg on 2010-12-15
what happens if you kill x? this is not an ideal solution, but it's better than pushing the computer's restart button.

```
sudo killall Xorg
```

can you read any of the writing on the "messed-up console like monoscript all over it" ?

---

### Post by svaens on 2010-12-15
Hi, 

sorry, I was being rather vague. 

If i kill X, then, as you wondered, yes, it allows me to semi-recover  .. (if you consider having all my X-applications terminated, recovering).

Seems like this problem only occurs when compiz is enabled.
Turning desktop effects off, has the result of 'fixing' the problem. 

I can live without desktop effects, ... in any case, there was another more pressing reason to turn it off (it didn't play well with eclipse).

---

### Post by azzid on 2010-12-15
> **afrodeity said:**
> Hi earthpigg, at least you can confirm its not some new feature or something which is deprecated?

More or less already answered, but ctrl+alt+f7 works fine in lucid.

I have had a similar issue, but with Debian, where ctrl+alt+f7 does not work, but alt+f7 does (there it is not a bug, but a feature). On my lucid install both (with or withour ctrl) works, so it (without ctrl) might be worth a try.

---

### Post by afrodeity on 2010-12-18
Just a note, the maverick upgrade appears to have fixed my problem, so it was just Lucid which had the bug for me. Hope you all come right.

PS: Have you tried using other F keys, like F8 or F9 to return to X?

---

