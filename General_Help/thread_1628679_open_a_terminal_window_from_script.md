---
title: "open a terminal window from script"
date: 2010-11-22
forum: General Help
---

### Post by bitttttor on 2010-11-22
Hi,
This should be easy but can't figure it out...

What should I put in a .sh script so when I execute it a new terminal window appears?

and, maybe more difficult

If I have a terminal window open, can pass text to it from a .sh by executing it?


thanks

---

### Post by SeijiSensei on 2010-11-23
> **bitttttor said:**
> What should I put in a .sh script so when I execute it a new terminal window appears?

In Ubuntu, I'd use 

```
gnome-terminal &
```

In Kubuntu, I'd use

```
konsole &
```

In each case I call the standard terminal application and run it in the background with a trailing "&".

> If I have a terminal window open, can pass text to it from a .sh by executing it?

That's harder. You can write to /dev/sysout in the same terminal session, but I don't know how to force it to display in another session appearing in a different window.  You might be able to use something like the "-display" option in X, or there might be equivalent options in GNOME or KDE.  I don't do that sort of thing myself, but these are a couple of avenues you might explore.

---

### Post by bitttttor on 2010-11-23
Great, thaks

---

