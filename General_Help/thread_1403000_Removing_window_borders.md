---
title: "Removing window borders"
date: 2010-02-09
forum: General Help
---

### Post by KameZero on 2010-02-09
Is there anyway to remove window borders in Ubuntu? Something like the right click - > undecorate window like in openbox is mostly what I'm looking for.

---

### Post by ubunterooster on 2010-02-09
use emerald, I haven't tried but w/ all the options it's bound to be able to do it. (or mess up emerald's dependencies, it did that to me when I removed too many things)

---

### Post by KameZero on 2010-02-14
Bump.

Anyone got any ideas on this?

---

### Post by howefield on 2010-02-15
Is this something you want to toggle on/off ?

If so, I'm not sure about that, but you could modify the borders of your chosen theme.

Eg, I use HumanLogin window borders, but edit the .xml file to reduce the border thickness to a pin stripe.

```
gksudo gedit /usr/share/themes/HumanLogin/metacity-1/metacity-theme-1.xml
```

---

