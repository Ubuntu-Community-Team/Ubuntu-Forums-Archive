---
title: "gvfsd-htt TCP connecting to barbadine.canonical.com and return &quot;it works&quot;"
date: 2011-12-22
forum: General Help
---

### Post by andrey_ on 2011-12-22
Hi, 
I noticed when I run "lsof -i" that gvfsd is connecting to [barbadine.canonical.com]("http://barbadine.canonical.com") (which returns : "it works"), I searched the web but there is no answer, what could that be? please help

> gvfsd-htt 26243 andrey    7u  IPv4 1225539      0t0  TCP ubuntu.local:38958->barbadine.canonical.com:www (CLOSE_WAIT)
gvfsd-htt 26243 andrey    9u  IPv4 1224257      0t0  TCP ubuntu.local:38950->barbadine.canonical.com:www (CLOSE_WAIT)
gvfsd-htt 26243 andrey   11u  IPv4 1209570      0t0  TCP ubuntu.local:38894->barbadine.canonical.com:www (CLOSE_WAIT)
gvfsd-htt 26243 andrey   13u  IPv4 1225131      0t0  TCP ubuntu.local:38952->barbadine.canonical.com:www (CLOSE_WAIT)

---

