---
title: "Bamboo Pen &amp; Touch problems in 11.04?"
date: 2011-09-10
forum: General Help
---

### Post by bobtheflyingmonkey on 2011-09-10
I have a Wacom Bamboo Pen & Touch, the actual pen works mostly how it should, but the touch is hardly functional at all (I'd actually like to remove touch if at all possible) and I don't know how to configure the buttons which seem to have changed functions on their own at random.
Anyone feel like helping?

---

### Post by Favux on 2011-09-10
Hi bobtheflyingmonkey,

Welcome to Ubuntu forums!

It is most likely related to your model.  Enter in a terminal:
```
lsusb
```
The Wacom line will tell the tale.  The 5 (6?) newer ones use a different USB protocol.  The good news is Chris just figured it out and has submitted a fix to the kernel for touch.

In the meantime there are several ways to shut touch off including the touch toggle script on the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562").  Also I link to the first version of Chris' wacom.ko touch patch near the top.

In addition Chris has been working on some gesture updates and I've tested the scroll and zoom for instance.  They're really working much better.  So a lot of goodies coming

---

