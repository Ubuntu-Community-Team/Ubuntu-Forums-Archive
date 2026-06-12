---
title: "Firefox is acting"
date: 2009-08-12
forum: General Help
---

### Post by triplesick on 2009-08-12
Ubuntu 9.04, Firefox for Ubuntu 3.0.13 as received through automatic update.

On some webpages, if I try to use the arrow keys to scroll up and down, Firefox, instead of scrolling up or down, spazmatically scrolls to whatever part of the page it feels like.  It might suddenly scroll all the way down or all the up, or not scroll at all, and weirdest of all is that the page down button on such pages makes it scroll to just below the top of the page, regardless of how many times I press it.  Other pages it works fine.

WTF, man?  Ima sick some hounds on this fox.

---

### Post by lovinglinux on 2009-08-12
Close Firefox, then run the command below to open Firefox Profile Manager:

```
firefox -P
```

Then create a new profile from there and start Firefox using it. Check if the problem persists. If yes, then we know is not a profile related problem. If not, then close Firefox and start your normal profile with this command:

```
firefox -safe-mode
```

Check if the problem persists. If not, then problem is caused by an extension. If the problem persists, then check Firefox settings.

---

