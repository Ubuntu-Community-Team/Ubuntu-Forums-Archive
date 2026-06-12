---
title: "Keyboard weirdness"
date: 2010-04-30
forum: General Help
---

### Post by TimsterC on 2010-04-30
Hi Folks,
I had this problem in 9.10 as well but it's still there with 10.4
Machine : Lenove ThinkPad W500
OS : Ubuntu Desktop 32 bit
Problem:
I have the keyboard layout set to UK and the region is set to UK
Whenever I try to enter a @(at symbol) by holding shift and the '(apostrophe) key I don't get the @. Instead I get the &#937;(Omega) symbol.
Has anyone seen this before?
It was worse with 9.10 as the Delete key did not work either. Very odd.

All the other keys work and are the standard UK layout. e.g. £ works fine
Also I tested it during the install and it worked fine and the @ key worked fine too.

Please can someone give me a clue as to how to solve this, it's messing with my head now.

Thanks in advance.

TimC ;o)

---

### Post by Eraemaajaervi on 2010-04-30
did you try another model? (option in the keyboard layout settings)

---

### Post by TimsterC on 2010-04-30
yes, tried lots of them.
I think it may be something to do with Synergy / Synergy+

---

### Post by TimsterC on 2010-04-30
FIXED

Just added the following command to the startup scripts and it works fine.
xmodmap -e "keycode 24 = q Q at at at at"

This solves my problem. [Found on the Synergy+ issues page here.]("http://code.google.com/p/synergy-plus/issues/detail?id=62&colspec=ID%20Stars%20Type%20Status%20Priority%20Milestone%20Owner%20Summary")

---

