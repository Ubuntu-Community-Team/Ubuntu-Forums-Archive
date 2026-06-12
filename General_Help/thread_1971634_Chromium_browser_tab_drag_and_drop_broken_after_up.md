---
title: "Chromium browser tab drag and drop broken after upgrade to 12.04"
date: 2012-05-02
forum: General Help
---

### Post by tonysidaway on 2012-05-02
Under Unity after upgrading to 12.04, drag and drop of existing browser tabs in Chromium browser appears to be broken. The tab always moves to a new window, no matter where it is dropped on the existing Chromium window. This appears to be an unwanted interaction between the drag and drop functionalities of Chromium and Unity. Formerly I was routinely able to reorder tabs in the Chromium window using drag and drop.

I'm running Chromium 18.0.1025.151 (Developer Build 130497 Linux) Ubuntu 12.04. This problem shows up under the standard login, and switching to Ubuntu 2D doesn't help. Clearing my local ~/.cache/chromium and ~/.config/chromium directories to restart Chromium "clean" doesn't help either.

Switching to an alternative login session using a minimalist window manager, dwm, solves the problem. Note that dwm has no built-in drag and drop functionality to clash with Chromium's.

I've searched hard here and elsewhere for any other references to this problem, which I've encountered only since upgrading to 12.04 the other day. Has anybody else found this? Is there a way to turn off whatever Unity is doing and let Chromium do its stuff?

---

### Post by cdar07 on 2012-05-03
Me too :/

Here is bug page:
[http://code.google.com/p/chromium/issues/detail?id=124761](http://code.google.com/p/chromium/issues/detail?id=124761)

---

### Post by pbradaric on 2012-05-08
I can confirm this too but with Google Chrome (didn't try Chromium).

---

### Post by tonysidaway on 2012-05-08
I got so fed up with this that I switched to dwm for good. Chromium works very well in that environment.

---

### Post by bootch777 on 2012-09-23
Faced the same issue. When i drag a tab it is separated into a separate window and does not stick back.
Ubuntu 12.04 x64, latest updates
Unity 2D
Chromium 20.0.1132.47 Ubuntu 12.04 (144678)

---

### Post by meditatingfrog on 2012-10-27
Same problem using fluxbox and chromium-browser on 12.04.

---

