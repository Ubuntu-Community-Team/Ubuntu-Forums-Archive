---
title: "packagesearch problem"
date: 2009-10-12
forum: General Help
---

### Post by L_V on 2009-10-12
packagesearch V2.4 is working fine in Debian/KDE4.3.
It is possible to install/remove packages.

packagesearch V2.4 does not work correctly in Ubuntu/KDE4.3.
Installing or removing a package should normally open a konsole.
No effect in Ubuntu.

kdesudo is correctly configured.

Who can confirm this bug ?

---

### Post by L_V on 2009-10-17
Bug confirmed: [url=http://www.mail-archive.com/debian-qt-kde@lists.debian.org/msg27434.html]
_Processed: konsole: Does not support -T option as required by the policy_[/url]

[url=http://groups.google.com/group/linux.debian.bugs.dist/browse_thread/thread/a4687986adb5a51e]
Bug#539255: packagesearch: No messages given on install or update errors [/url]

---

