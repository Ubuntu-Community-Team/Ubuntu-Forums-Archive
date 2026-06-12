---
title: "Graphical Bug"
date: 2012-04-21
forum: General Help
---

### Post by jrisreal on 2012-04-21
Please help.  There is an annoying graphical bug in my copy of xubuntu (11.10 64-Bit) that has occurred many times.  It doesn't cause any functionality issues, but it is rather annoying to see it.  Randomly, a block at the top left of the screen will freeze up and continue to display whatever was occupying that space when it occurred.  Here is an image of what I am talking about:

---

### Post by jrisreal on 2012-04-21
anybody?

---

### Post by brainwash on 2012-04-22
Did you place another panel on the left side? Just wondering, because the size of the shown artifact and the size of the gap between the window and the left border seems to be the same.

Furthermore, you should check ~/.xsession-errors if the bug occurs again:
```
tail -n 20  ~/.xsession-errors
```

---

### Post by jrisreal on 2012-04-22
I didn't add or remove any panels...the desktop is almost exactly how xubuntu comes default

---

### Post by LewisTM on 2012-04-24
I'm experiencing a similar bug. A white, semi-transparent square at the top left. 

This is recent, I'd say one or two days.
It doesn't keep me up at night but I'm curious about what's behind that.

A restart of Xfwm4 removes it.

---

### Post by jrisreal on 2012-04-30
It seems that this bug only happens when I have frostwire open.  As soon as I close it, the box goes away...this changes the story just a bit.

---

### Post by dr zaius on 2012-07-22
I'm experiencing the same issue. In my case it seems that a java application might be the cause for the issue. I tried this with different ones (e.g. JDownloader and PlaystationMediaServer) where the problem occures. On the other hand, Freemind, which is also Java based, does not trigger the problem. Maybe this is helpful? :)

---

