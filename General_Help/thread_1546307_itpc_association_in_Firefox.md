---
title: "itpc association in Firefox?"
date: 2010-08-05
forum: General Help
---

### Post by Muskiet on 2010-08-05
I'd love to download a certain podcast but when clicking on the ITunes button I get [I]"Firefox doesn't know how to open this address, because the protocol (itpc) isn't associated with any program."
[/I]How do I associate itpc links to a program like Rhythmbox?
I have Ubuntu 10.04 installed.

---

### Post by gordintoronto on 2010-08-05
I use Miro as my Podcatcher. When I'm on a podcast site, I click on "RSS feed" and everything works just fine.

You might try Googling: itunes linux

---

### Post by NoBugs! on 2010-08-11
To set this protocol, go to Alt-F2, run "gconf-editor".
The settings for itpc protocol are in /desktop/gnome/url-handlers/itpc

You can also change the itpc:// to http:// to get to the podcast.

---

