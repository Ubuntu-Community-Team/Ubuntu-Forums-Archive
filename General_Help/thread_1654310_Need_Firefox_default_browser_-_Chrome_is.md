---
title: "Need Firefox default browser - Chrome is?"
date: 2010-12-28
forum: General Help
---

### Post by dorlow on 2010-12-28
I tried Chrome, but I still like Firefox better.  I can't figure out how to get Firefox back as the default browser.  When I go to Preferences --> Prefered Applications, web browser is set to Firefox.  I found this post...

[http://ubuntuforums.org/showthread.php?p=10228552](http://ubuntuforums.org/showthread.php?p=10228552)

They said to run this command...

```

sudo update-alternatives --config x-www-browser

```Tried that and it didn't help either.  When clicking on link icons on my desktop, they open up in Chrome.  Chrome says something to the extent "chrome is not your default browser to open links with.  Do you want to make it?"  I selected No and checked the box to not show it again.  (That's why the above is not exactly what it said.)  Kind of funny it said that yet it still opened up with Chrome and not Firefox.  Any ideas?

---

### Post by amsterdamharu on 2010-12-28
What if you open firefox and choose edit -> preferences -> advanced tab -> click "Always check if Firefox is the default browser on startup"
Then restart Firefox and set it to default.

---

### Post by dorlow on 2010-12-28
That didn't work.  I went to Preferences --> Advanced --> the box to have firefox to always check it's the default browser on startup was already checked.  I clicked the button "Check Now" and it says "Firefox is already your default web browser."  But when I click the URLs on the desktop, they still open with Chrome.

---

### Post by amsterdamharu on 2010-12-28
Right click the Icon and choose properties then click on the "open with" tab, choose firefox and click close.
Maybe that will help.

---

### Post by dorlow on 2010-12-28
There is no "open with" tab.  It's a mute point now though.  I figured out how to uninstall Chrome.

---

