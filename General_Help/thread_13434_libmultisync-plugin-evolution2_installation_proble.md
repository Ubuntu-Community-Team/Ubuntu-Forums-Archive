---
title: "libmultisync-plugin-evolution2 installation problem"
date: 2005-01-31
forum: General Help
---

### Post by LazyFool on 2005-01-31
Hi,

I'd like to install mulitsync and the corresponding Evolution2 plugin. Unfortunately the installation process fails due to unresolvable dependencies. These are the requested packages:
libebook8
libecal6
libedata-book1
libedata-cal5
libedataserver3

Meanwhile I figured out that these libs are in the evolution-data-server package which I've installed. Among others the following files are provided by the package:
/usr/lib/libebook.so.8
/usr/lib/libecal.so.6
/usr/lib/libedata-book.so.1
/usr/lib/libedata-cal.so.5
/usr/lib/libedataserver.so.3
/usr/lib/libegroupwise.so.6

Looks to me as if these are the sought-after libraries. Is this assumption right?
If yes, how do I get apt to accept evolution-data-server as the solution for the above mentioned dependencies?

Thanks for helping!
Best regards, LazyFool

---

