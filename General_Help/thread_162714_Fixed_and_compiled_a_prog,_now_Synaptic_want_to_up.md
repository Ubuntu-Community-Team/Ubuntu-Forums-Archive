---
title: "Fixed and compiled a prog, now Synaptic want to upgrade it to the unfixed version"
date: 2006-04-19
forum: General Help
---

### Post by jazzmuzik on 2006-04-19
In Breezy there was a bug in Noteedit. I believe I mentioned it in another thread. Anyway, I fixed it in source code, recompiled the package to a deb file and reinstalled it. All is well with Noteedit. But now Synaptic wants to upgrade noteedit to the one it thinks I should have even though they are the same version number. It's like the unrepaired version is competing with the fixed version. I've "locked" noteedit in Synaptic, but that doesn't matter. So every time I boot up the "Software Updates" program keeps reminding me of this available update. Is there a way to avoid this? Maybe I should have incremented the notedit version number or something in the deb package?

---

### Post by towsonu2003 on 2006-04-20
> **jazzmuzik]In Breezy there was a bug in Noteedit. I believe I mentioned it in another thread.[/quote]
did you file a bug report?   said:**
> Anyway, I fixed it in source code, recompiled the package to a deb file and reinstalled it. All is well with Noteedit. But now Synaptic wants to upgrade noteedit to the one it thinks I should have even though they are the same version number. It's like the unrepaired version is competing with the fixed version.
are you sure it's locked? do you see the lock "icon" when you highlight the package, to the left of the package name? "lock version" / "pinning" is supposed to work in such situations

also see [http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version) section 3.10

---

### Post by Pausanias on 2006-05-19
I can confirm this problem in breezy as well as dapper.

---

