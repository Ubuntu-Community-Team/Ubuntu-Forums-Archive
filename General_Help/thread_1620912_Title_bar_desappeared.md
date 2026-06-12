---
title: "Title bar desappeared"
date: 2010-11-13
forum: General Help
---

### Post by Isidorito on 2010-11-13
Before anythig... i was looking in other topics, but the solutions of its are not the solution im looking for.

I was installing lots of packages to my Ubuntu 10.10, going with the guide of ubuntulife.

I have a nvide geforce 8400 gs

The problem:

When i activates the "Extra" effects, the windows became a squarem losing the title bar, so, now i havent the "-, square, x" buttons.

If i change the effects to "none" the buttons come back, so i have a "solution" but i whant to have the effects in my pc.

Can anybody help me?

thanks!

---

### Post by pizza-is-good on 2010-11-13
A common problem. This happened to me a couple of releases ago (9.04 I believe).
Basically when you activate the effects, the window decorator goes bad.

While I attempt to dig up that old thread, go to your software center and install 'compiz' and 'compiz-fusion icon'.

---

### Post by pizza-is-good on 2010-11-13
OK, found that old thread.
It is [here]("http://ubuntuforums.org/showthread.php?t=1201112"). It was a similar problem. Try the solutions there and see if it works. Post back with some results...

Good luck!

~pizza

---

### Post by Isidorito on 2010-11-14
I solved it unninstalling compiz and installing the last driver of nvidia (I have an 840 gs) well.. more or less, no i cant select diferents qualitys of graphics now... seems like i will need to install compiz again

---

### Post by sikander3786 on 2010-11-14
Fusion-icon works for me and it has already been suggested. Add it to your startup and reload window manager whenever your title bars disappear. Fusion-icon sits in system tray so not hard to do that.

Alternatively, you can always press Alt + F2 and type

```
compiz --replace
```

to correct the problem whenever it happens.

Good Luck!

---

