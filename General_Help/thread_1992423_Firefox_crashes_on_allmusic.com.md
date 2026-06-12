---
title: "Firefox crashes on allmusic.com"
date: 2012-05-31
forum: General Help
---

### Post by pickarooney on 2012-05-31
I'm not sure if this is unique to my machine but every time I go to the new, revamped [www.allmusic.com](www.allmusic.com) site, it crashes within a couple of seconds.

Running it from the command line I get the following:

```
ACR (Component): component init
###!!! ABORT: X_ShmPutImage: BadMatch (invalid parameter attributes); 49 requests ago: file /build/buildd/firefox-11.0+build1/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 190
###!!! ABORT: X_ShmPutImage: BadMatch (invalid parameter attributes); 49 requests ago: file /build/buildd/firefox-11.0+build1/build-tree/mozilla/toolkit/xre/nsX11ErrorHandler.cpp, line 190
```

Does this happen to anyone else and/or is the above error in any way helpful in debugging?

---

### Post by Rodney9 on 2012-05-31
[http://www.allmusic.com/](http://www.allmusic.com/) works for me with Firefox 12

Others having similar problems with Firefox 11 -

[http://forums.mozillazine.org/viewtopic.php?f=9&t=2455253](http://forums.mozillazine.org/viewtopic.php?f=9&t=2455253)
[http://forums.mozillazine.org/viewtopic.php?f=38&t=2464901&start=15](http://forums.mozillazine.org/viewtopic.php?f=38&t=2464901&start=15)

I'm sorry I don't have any answers, maybe an upgrade to version 12 might help.

Rodney

---

### Post by pickarooney on 2012-05-31
hmm, to view the site, update the browser, to update the browser, reinstall a newer OS... I can see where this is going :D

---

### Post by Frogs Hair on 2012-05-31
I am on 12.04 and tested the site with Opera , Iron, and Firefox Nightly with success. If you are using 10.10 which is reached end of life as your info states any PPAS for newer FF versions are probably no longer supported.

---

### Post by pickarooney on 2012-06-02
I tried it in safe mode and it froze my whole PC - had to reset.
My bank site causes a crash every time as well, in safe or normal mode:

```

java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.13) (6b20-1.9.13-0ubuntu1~10.10.1)
OpenJDK Server VM (build 19.0-b09, mixed mode)
Java detection applet ...
Exception in thread "Thread-6" java.lang.NullPointerException
	at sun.applet.AppletPanel.showAppletStatus(AppletPanel.java:947)
	at sun.applet.AppletPanel.run(AppletPanel.java:607)
	at java.lang.Thread.run(Thread.java:636)
Environment detection applet version 1.0.2
Application version : Dictao Brooklyn library 4.5
AdConfig version 4.5.0.0
Assertion failure: rt->onOwnerThread(), at /build/buildd/firefox-11.0+build1/build-tree/mozilla/js/src/jsapi.cpp:6317

```

I must give Opera a go...

Well, it works, but I can't be dealing with the tab bar eating up 10cm of screen space and all those ads... yuck!

---

### Post by pickarooney on 2012-06-02
Has anyone a guide to installing FF 12 via SVN or compiling it?

---

### Post by pickarooney on 2012-06-02
<snip> I upgraded to Natty just so I could install FF12 and, along with all the other things broken in the upgrade, FF still crashes exactly the same way.

---

### Post by pickarooney on 2012-06-04
Problem is in preferences.js. Creating a new profile and importing elements piecemeal from the old one helped me identify the issue (more or less).

---

