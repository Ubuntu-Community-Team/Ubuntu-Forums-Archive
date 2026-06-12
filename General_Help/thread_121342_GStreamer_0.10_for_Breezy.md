---
title: "GStreamer 0.10 for Breezy?"
date: 2006-01-24
forum: General Help
---

### Post by tman_ubuntu on 2006-01-24
Will Ubuntu have a GStreamer 0.10 update available for Breezy or will they wait to roll it with Dapper?  I believe the GStreamer team is releasing the new version as stable so does that mean we will see a updated version for Breezy as well?

---

### Post by RAOF on 2006-01-25
[QUOTE=tman_ubuntu]Will Ubuntu have a GStreamer 0.10 update available for Breezy or will they wait to roll it with Dapper?  I believe the GStreamer team is releasing the new version as stable so does that mean we will see a updated version for Breezy as well?[/QUOTE]
No.  The Ubuntu policy is essentially "bugfixes only" after the Ubuntu version (ie: Breezy/5.10) has been finalised.  It may or may not enter the unofficial backports repository, but I doubt it - it might be too time consuming to backport properly (That's why you don't see a Firefox 1.5 package in the backports repository).

---

### Post by doclivingston on 2006-01-25
Having gstreamer 0.10 for Breezy would be useless unless you also got backports of the applications to support it. That would mean Totem 1.3.0, Sound-Juicer 2.13.3, Rhythmbox from cvs, Banshee 0.10.something, etc. Some of those applications may not work on Breezy without newer versions of other libraries that wouldn't be backported.

If you really want gstreamer 0.10 on Breezy, I imagine that you will have to build it yourself (or find someone who had, and made packages).

---

