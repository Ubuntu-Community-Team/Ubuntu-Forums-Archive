---
title: "&quot;Shut Down Button&quot;"
date: 2012-01-21
forum: General Help
---

### Post by RogerDavis on 2012-01-21
Somehow I deleted my pre-installed Shut Down Button.  I was able to add another from the "Add to Panel" function, but it doesn't work the same.  The original was a quick drop-down with selections.  The re-added one is a new window, with fewer choices, I think.

How do I get the original button back?

Thanks!

---

### Post by Tamlynmac on 2012-01-21
There's two shutdown applets in the add to panel.
1. Shut Down Applet
2. Indicator Applet Session (which includes desktop name)

I believe the indicator applet session (uses the shut down applet and the desktop name for account charting) is the original that appears in the top right hand corner of the panel when Ubuntu is first installed. It's a dual purpose applet. If left clicked on the desktop name (just to the left of the icon) another drop down menu appears with info regarding charting accounts, status, guests, etc. If left clicked on the indicator icon the *shut down applet drop down menu will appear.

* The shut down applet is a single icon with a simple drop down menu for multiple options including log out, hibernate, restart, shut down, etc.

I also believe both applets (shut down) drop down menus are identical. As they both use the shut down applet.  

Hope this helps

---

### Post by RogerDavis on 2012-01-21
I can get to The GNOME Panel 2.30.2 window, with no drop down options.  

I can get to Indicator Applet 0.3.7, with no drop down options.  

I purposely deleted what I believe is the desktop name, because I can easily tell who is logged in without it and needed the space, so I can't follow your specific directions.

I am able to open an "Add to Panel" window, which is where I found the less functional icon with only the three choices of "Shut Down", "Restart", and "Hibernate".

I was able to add an "Indicator Applet Session" which included the icon I was missing" POOF !.

So now, how do I get rid of the "User" part, as I don't need it and it has no "live" functions (all are dimmed and unselectable).  It may have to do with chat functions, which I don't use anyway.

Thanks!

---

### Post by Tamlynmac on 2012-01-21
> RogerDavis
So now, how do I get rid of the "User" part, as I don't need it and it  has no "live" functions (all are dimmed and unselectable).

I don't know. Hopefully, another member will have an answer. At least now your back to the default shutdown (original) menu.
Poof! :D

There's no reason you must remove the "User" part, other than the small foot print in the panel. Did you some how find a way to remove it before, or is it just now that you've considered doing so? Either way, good luck and sorry I can't help further.

Mac

---

### Post by BC59 on 2012-01-21
You could try to run:

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

