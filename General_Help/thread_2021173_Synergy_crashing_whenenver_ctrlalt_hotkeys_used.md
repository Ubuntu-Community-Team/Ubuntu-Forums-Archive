---
title: "Synergy crashing whenenver ctrl/alt hotkeys used"
date: 2012-07-08
forum: General Help
---

### Post by redherring1 on 2012-07-08
I'm trying to connect an Ubuntu client to a Windows 7 Synergy server, and whenever I use a hotkey such as alt+tab or ctrl+c, the ubuntu synergyc client crashes.  This behavior is mirrored whether I'm using Quicksynergy or typing synergyc <serveraddress> into the CLI.  The server is 1.3.8 32-bit, and the client I believe is 1.3.x, or whatever is available through the ubuntu repos.  Any ideas as to what could be causing this behavior? 


EDIT: I solved this by downloading the latest stable .deb package from [www.synergy-foss.org]("http://www.synergy-foss.org")

---

### Post by redherring1 on 2012-07-09
Nevermind, the behavior has resumed today after I restarted...  Any ideas again?  :(

---

### Post by redherring1 on 2012-07-10
Did some more googling, apparently this is a known issue: [https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/926198](https://bugs.launchpad.net/ubuntu/+source/synergy/+bug/926198)

Switching to the 1.4.x beta should solve this issue, but if you're like me and it created other, equally distressing bugs, you can download the modified code at the bottom of the link above and that solved the issue while allowing me to remain on version 1.3.

---

