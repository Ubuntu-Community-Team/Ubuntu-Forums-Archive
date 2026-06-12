---
title: "Projector and ubuntu"
date: 2010-09-29
forum: General Help
---

### Post by oleink on 2010-09-29
Hey I was wondering how Ubuntu does with projectors.  Can I do anything to get my impress presentations on the projector or should I just use the bios FN F8 key combination?

---

### Post by P4man on 2010-09-30
That is videocard/driver dependent. Do you know what card you have?
If you didnt install a restricted videocard driver for ATI or nVidia, you should be able to configure the projector after connecting it, in system > preferences > display. Otherwise its in the ATI or nVidia settings. You probably want to clone the image.

If that doesnt seem to work, then open a terminal and copy paste the output of

```
xrandr | grep connected 
``` 

(also do this while the projector is connected).

---

### Post by oleink on 2010-09-30
> **P4man said:**
> That is videocard/driver dependent. Do you know what card you have?
If you didnt install a restricted videocard driver for ATI or nVidia, you should be able to configure the projector after connecting it, in system > preferences > display. Otherwise its in the ATI or nVidia settings. You probably want to clone the image.

If that doesnt seem to work, then open a terminal and copy paste the output of

```
xrandr | grep connected 
``` 

(also do this while the projector is connected).

alrighty.  I've got an old ati x1270.  Did you mean System>Preferences>Display?

---

