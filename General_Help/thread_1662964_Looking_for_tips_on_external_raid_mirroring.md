---
title: "Looking for tips on external raid mirroring"
date: 2011-01-09
forum: General Help
---

### Post by shinobitux on 2011-01-09
Hello, looking for advice on how best to mirror two external raid 5 or 6 arrays. If I'm in the wrong forum, let me know.

For example, two fibre-attached storage arrays connected to a central server and using software raid (mdadm for example), mirroring.

For the purposes of this thread, consider this a contrived example. The "why?" is not that important and, yes, I need them to be mirrored. The way the arrays are connected to the server is unimportant to me. They simply need to be completely separate from each other. Eventually, I may try something with mounting over nfs so I can put them in different buildings...but that's for another time...

What's the best way to accomplish this?

Is there a Linux file system that I can use instead of a software raid to mirror?

If the central server dies and is unrecoverable can a 2nd be set up and configured to talk to the two remote arrays? (Trying to avoid single point of failure)

---

