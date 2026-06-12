---
title: "Cannot do a lowercase É (eacute) with us_intl since Maverick"
date: 2010-10-12
forum: General Help
---

### Post by bobatomik on 2010-10-12
I am a big fan of us_intl AltGr dead keys, but since I upgraded to Maverick, I can&#8217;t do a lowercase É with is the level 3 on « e »

Instead, it does the eurosign « &#8364; »

I tried adding this line 
   key <AD03> { [        e, E,           eacute,   Eacute      ] };
to /usr/share/X11/xkb/symbols/us

in the correct section, but it changed nothing

---

### Post by sendblink23 on 2010-10-12
> **bobatomik said:**
> I am a big fan of us_intl AltGr dead keys, but since I upgraded to Maverick, I can’t do a lowercase É with is the level 3 on « e »

Instead, it does the eurosign « € »

I tried adding this line 
   key <AD03> { [        e, E,           eacute,   Eacute      ] };
to /usr/share/X11/xkb/symbols/us

in the correct section, but it changed nothing

Buu I know its a pain... I just use the Character Map when I need the certain letter

---

### Post by bobatomik on 2010-10-13
Finally found it

This is caused by typo(base) symbols

which is included if you check misc compat options » extra typo

Cheers

---

### Post by sendblink23 on 2010-10-13
> **bobatomik said:**
> Finally found it

This is caused by typo(base) symbols

which is included if you check misc compat options » extra typo

Cheers

oh cool ;) I'm gonna check that out

---

