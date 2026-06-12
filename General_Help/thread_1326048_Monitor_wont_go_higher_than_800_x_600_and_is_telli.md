---
title: "Monitor wont go higher than 800 x 600 and is telling me it is an unknown monitor"
date: 2009-11-14
forum: General Help
---

### Post by ds900 on 2009-11-14
I have an IBM E74 monitor, don't know about the graphics card or anything (bit of a n00b)
Can n e 1 help me?

---

### Post by CoryThompson on 2009-11-14
It's a bit hard with the lack of details you are giving us. All i can suggest is to try to open up display settings (System -> Preferences -> Display) and click on detect. 

If this doesn't work try finding out graphics card type because chances are you will need to install appropriate drivers.

To find out graphics card you can open your pc and it usually has a model number which you can google or consult your user manual.

---

### Post by ianc on 2009-11-14
Before taking it apart you could try opening a terminal (Applications - Accessories - Terminal) and typing:

```
lspci | grep -i graphics
```

That should identify it - once you've done that try a forum search to see if others have had similar problems.

---

### Post by CoryThompson on 2009-11-14
That is way more practical then my idea :p

---

