---
title: "Multiple Web Services on Same Port?"
date: 2010-05-07
forum: General Help
---

### Post by brianafischer on 2010-05-07
Hello,

I am currently running MythTV, SubSonic, and SABnzbd on my Ubuntu server.  I would like to open up some of these services through my hardware firewall.  The preference would be to host all of these on the same port, but each with a different context path:

For instance:
[LIST][*][http://localhost/subsonic](http://localhost/subsonic)
[*][http://localhost/sabnzbd](http://localhost/sabnzbd)
[*][http://localhost/mythweb](http://localhost/mythweb)
[/LIST]

I tried this, but it seems that sabnzbd blocked the other items from working.

Any advice?

Thanks!

---

