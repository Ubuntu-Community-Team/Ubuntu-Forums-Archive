---
title: "Lubuntu - To Reset Double-Click Speed"
date: 2012-02-05
forum: General Help
---

### Post by 2CV67 on 2012-02-05
Just ironing out the last (I hope...) wrinkles in my new Lubuntu.

I want to reset the double-click speed to a different value.

Up till Lubuntu, that has always been a very quick GUI operation, with a test panel to set the time with a slider & something to tell if you got it or not.

Incredibly (I hope somebody will tell me otherwise) there does not seem to be any GUI for this in Lubuntu.

After a lot of searching, I found advice to tinker with Menu > System Tools > Configuration Editor > desktop > gnome > peripherals > mouse > double_click > XXX but none of the actions in that mouse section had any effect at all.

Finally (so far) I tracked down a method in the LXDE.org Forum which does work, but is not exactly convenient.

I attach it below as a tentative HOW TO in case anybody else can benefit.
It is hardly convenient; as far as I could tell, for every change you want to test, you have to: Open a hidden file > change a numerical value > save the file > logout > login > open file manager > test...

Please feel free to correct any errors in this HOW TO or, preferably, show me a better way!

Thanks!

**HOW TO: Change Double-Click Speed in Lubuntu** 
*(basically copied from LXDE.org Forum with my thanks)*

> Find the hidden text file ".gtkrc-2.0" in your home directory. If it does not exist, create it. If it does exist, read it before you proceed -- it may advise you to use ".gtkrc-2.0.mine" instead.

Add the following line:

```
gtk-double-click-time=1000
```

That increases the allowed interval between two clicks from its default (250 milliseconds) to a full second (1000 milliseconds).

Save file & logout & login to test the change.

---

### Post by ssulaco on 2013-01-05
Thanks,That did it.

---

