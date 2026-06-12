---
title: "'Options' tab missing form gnome-session-properties (aka Startup Applications)"
date: 2011-07-26
forum: General Help
---

### Post by pium on 2011-07-26
Hi all,

I steal the title from this post: [http://ubuntuforums.org/showthread.php?t=1683893](http://ubuntuforums.org/showthread.php?t=1683893)

=> "Automatically remember running applications when logging out" is no longer existing because of bugs with multiple sessions.


Is there a way to enforce this option, even if it is bugged with multiple sessions? My system has only 1 user and I miss so much this feature.

Thanks you

-- pium

---

### Post by mc4man on 2011-07-26
It is also broken to a great extent w/ a single user, at least w/ the ubuntu login

If you must see than you'll need to rebuild the source, preferably as debian packages.
In that case you'd need to revert the 06_nuke... patch which is applied when you apt-get the source
Not worth the effort for a borked option, let alone the 500MB or so of build-deps

---

### Post by pium on 2011-07-29
ok... too bad.

Thanks for the reply

---

