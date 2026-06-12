---
title: "Authorization Required Box"
date: 2010-09-09
forum: General Help
---

### Post by lindsay7 on 2010-09-09
This just started showing up and I do not know how to get rid of it or what it means. Please give me an idea on what this is all about.

---

### Post by Ocxic on 2010-09-09
The website needs a username and password to perform an action you have requested.

This is most likely an internal error and can be safely ignored.

---

### Post by NearlyALaugh on 2010-09-09
Unless you're trying to open **localhost:45715** on purpose, something unusual is happening. I notice you have installed some add-ons to Firefox. Try running the browser in [safe mode](http://support.mozilla.com/en-US/kb/Safe+Mode) (extensions temporarily disabled) and see if the problem persists.

Close all open windows, and in a terminal type:```
firefox -safe-mode
```Visit a few pages. If the problem stops, it means one of your add-ons is causing the problem. If so, disable each extension individually—especially the last one you installed—until you find the one causing the problem.

Then you can try to debug it or ask its developer for support.

---

### Post by CharlesA on 2010-09-09
I suppose you could also run this is a terminal, just to check:

```
netstat -ln
```

---

### Post by lindsay7 on 2010-09-09
> **NearlyALaugh said:**
> Unless you're trying to open **localhost:45715** on purpose, something unusual is happening. I notice you have installed some add-ons to Firefox. Try running the browser in [safe mode](http://support.mozilla.com/en-US/kb/Safe+Mode) (extensions temporarily disabled) and see if the problem persists.

Close all open windows, and in a terminal type:```
firefox -safe-mode
```Visit a few pages. If the problem stops, it means one of your add-ons is causing the problem. If so, disable each extension individually&#8212;especially the last one you installed&#8212;until you find the one causing the problem.

Then you can try to debug it or ask its developer for support.

That did the trick, the problem child was something called "Bindwood" an extention to Firefox.  I have no idea where it came from but I deleted it and the Problem is solved.

Thank you very much for the great suggestion and everyones input.

---

