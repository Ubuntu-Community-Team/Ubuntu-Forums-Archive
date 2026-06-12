---
title: "error message"
date: 2010-12-28
forum: General Help
---

### Post by cmcanulty on 2010-12-28
Can someone explain to me how to fix this error

> W: Failed to fetch [http://debian.scribus.net/debian/dists/testing/Release](http://debian.scribus.net/debian/dists/testing/Release)  Unable to find expected entry  non-free/binary-i386/Packages in Meta-index file (malformed Release file?

---

### Post by QLee on 2010-12-28
> **cmcanulty said:**
> Can someone explain to me how to fix this error

Yes, don't try to download things from a Debian Squeeze (testing) repository to your Ubuntu system.

And by the way, that release file doesn't show any "non-free" binary packages, just as the error told you. It only shows packages from "main".

---

### Post by cmcanulty on 2010-12-28
OK thanks I removed that source, didn't know I had a testing source

---

### Post by QLee on 2010-12-29
[QUOTE=cmcanulty]OK thanks I removed that source, didn't know I had a testing source[/QUOTE]

Good. 
Judging by the info under your avatar, you wanted the one for maverick. Note: The one from the maverick directory only shows "main" too so don't include "non-free" on the line, but  you've probably already figured that out, I just came back on the forum. It's always a good idea to make sure what is available when writing source lines for packages from upstream sources.

---

