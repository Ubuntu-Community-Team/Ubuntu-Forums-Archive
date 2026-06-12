---
title: "Stale version of python-gdata"
date: 2011-07-11
forum: General Help
---

### Post by bkline on 2011-07-11
Ubuntu isn't generally behind the curve on keeping up with upstream packages, but that seems to be true with python-gdata, which is at version 2.0.8 on Natty, which doesn't support structured contact data from a Google address book (so, for example, instead of an articulated name with given name, family name, prefixes, suffixes, other names you just get back one string with everything mushed together, even though the back end has all of the structured information).  The current version of the APIs is v3.  Any timetable for when Ubuntu will catch up?

Thanks!

---

### Post by Lighthorse01 on 2011-09-11
Anyone seen  python-gdata 2.0.10 64-bit for Ubuntu ??

---

### Post by Lighthorse01 on 2011-09-11
Found 

[LIST]
[*]         [           python-gdata           2.0.8-1.1           in           amd64           (Release)         ]("https://launchpad.net/ubuntu/oneiric/amd64/python-gdata/2.0.8-1.1")
[*]         [           python-gdata           2.0.14-2           in           amd64           (Release)         ]("https://launchpad.net/ubuntu/oneiric/amd64/python-gdata/2.0.14-2")
[/LIST]

---

### Post by WorMzy on 2011-09-11
> **bkline said:**
> Ubuntu isn't generally behind the curve on keeping up with upstream packages.

Are you joking? Ubuntu tends to hold non-critical updates back for the next version of Ubuntu. The reason for this is that Ubuntu tends to focus on stability, rather than keeping up-to-date.

Oneiric will have python-gdata v2.0.14, but don't expect the Natty (or previous) repos to have anything other than what they currently contain, unless a serious security flaw is discovered.

You can download the official Oneiric package from here: [http://packages.ubuntu.com/oneiric/all/python-gdata/download](http://packages.ubuntu.com/oneiric/all/python-gdata/download)

If you want to keep up-to-date with upstream packages, you're using the wrong distro.

---

