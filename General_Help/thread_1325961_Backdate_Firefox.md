---
title: "Backdate Firefox"
date: 2009-11-13
forum: General Help
---

### Post by Ellaine on 2009-11-13
Just loaded Ubuntu 9.10 with Firefox 3.55 How can I backdate to Firefox 3.0.14 so I can install the Flash Capture plugins? Or are there new Clipta Toolbar, Flash Video Downloader, etc. for Firefox 3.55?  Please see [http://ubuntuforums.org/showthread.php?t=1292949](http://ubuntuforums.org/showthread.php?t=1292949)
rb0171610 answered this for firefox 3.0.14.  I'm looking for the same answer for firefox 3.5.5.

---

### Post by lidex on 2009-11-14
This works for me on Firefox 3.5.6:
[https://addons.mozilla.org/en-US/firefox/addon/3006]("https://addons.mozilla.org/en-US/firefox/addon/3006")

---

### Post by lovinglinux on 2009-11-14
> **Ellaine said:**
> Just loaded Ubuntu 9.10 with Firefox 3.55 How can I backdate to Firefox 3.0.14 so I can install the Flash Capture plugins? Or are there new Clipta Toolbar, Flash Video Downloader, etc. for Firefox 3.55?  Please see [http://ubuntuforums.org/showthread.php?t=1292949](http://ubuntuforums.org/showthread.php?t=1292949)
rb0171610 answered this for firefox 3.0.14.  I'm looking for the same answer for firefox 3.5.5.

Those are extensions, not plugins. Anyway, a quick search on [Mozilla Add-ons](https://addons.mozilla.org) database shows they are all compatible with Firefox 3.5.5. If they are showing as incompatible, try to update your extensions. A compatibility patch should be applied. If you still have incompatible extensions after the update, then you can try to force compatibility with [Nightly Tester Tools](https://addons.mozilla.org/en-US/firefox/addon/6543).

I don't recommend downgrading Firefox to 3.0.14. Firefox 3.5 series is a lot better.

---

### Post by Ellaine on 2009-11-14
lidex: Thanks a million; works fine but must be started each time. The older method in 3.0.14 added a clipta toolbar that I only needed to click on to download.:p

---

### Post by lidex on 2009-11-14
A couple of things you can do. Right-click on toolbar and select "customize". Drag the video download helper icon onto toolbar. You can right-click on that icon to get a bunch of options, in fact, in those options select "subtile extension>create your own toolbar". When video content is active, left-click on icon.

---

