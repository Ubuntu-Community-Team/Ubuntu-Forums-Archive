---
title: "lost ssl in WebKitGTK+"
date: 2011-02-12
forum: General Help
---

### Post by cowlitzron on 2011-02-12
I was using Ubuntu, Gnome desktop after installing several developmental files I lost SSL on WebKitGTK+.  This affected all WebKitGTK+ browsers, including Midori running WebKit 1.2.6 and dwb running 1.3.10.  When I run one of those browsers and I try to go to an https page I get the message   The page  "https://someurl" couldn't be loaded  SSL handshake failed.  Then, I installed the Xubuntu desktop and deleted the packages that are in Ubuntu but not in Xubuntu and I still have that problem.  The good news is that Firefox, Swiftfox and Opera are still loading https pages.  Does anyone know what could keep the WebKitGTK browsers from loading SSL on my system.

---

### Post by cowlitzron on 2011-02-14
It could have been that I have a beta version of libsoup2.4-1 that fails on ssl.  At this time I have version 2.33.1.  The Maverick repository has version 2.31.92.  I could switch to that version to see if I can get ssl to work in Midori and dwb.

---

### Post by cowlitzron on 2011-02-14
I switched back to the stable version of libsoup.  And, now I have ssl working again in Midori on WebKitGTK 1.2.6 and dwb on WebKitGTK 1.3.10.  The beta version must have been defective with ssl on WebKitGTK+ browsers.

---

