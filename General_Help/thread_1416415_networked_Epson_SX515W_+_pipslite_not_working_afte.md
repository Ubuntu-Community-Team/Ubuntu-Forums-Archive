---
title: "networked Epson SX515W + pipslite not working after karmic upgrade"
date: 2010-02-26
forum: General Help
---

### Post by xetum on 2010-02-26
I've a networked SX515W. Worked well in Jaunty with pipslite_1.4.0-5_i386.deb. Now in karmic every job stops with: "*/usr/lib/cups/filter/pipslite-wrapper failed*". Test page prints well
Have tried with Karmic live CD and problem persists
I think is an incompatibility with new CUPS 1.4.X (Jaunty was 1.3.9) and pipslite.
I've tried to dpkg-buildpackage from sources to link with libltdl7 instead of libltdl3 and problem persists.

Can somebody confirm that networked epson printer + pipslite + cups 1.4.X + karmic works?

Thanks

---

