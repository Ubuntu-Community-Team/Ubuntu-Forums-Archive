---
title: "Where are the Virtual Terminals?"
date: 2011-06-21
forum: General Help
---

### Post by jpaugh64 on 2011-06-21
How do I enable virtual terminals? Whenever I press Ctrl+Alt+F1 through F8, All I see is a blank screen, except on Ctrl+Alt+F7, which has the graphical session. After some digging through the Internet, I learned that the Sys V Init daemon uses /etc/inittab to configure them, and the new Upstart Init daemon uses /etc/event.d/ for this (at least on Fedora; link [here]("http://www.mail-archive.com/plug@plug.org/msg20991.html")).

However, I can't find inittab (as expected) or event.d (surprisingly). What's going on? More importantly, how do I configure the virtual terminals to start every boot-up?

I'm running Ubuntu 11.04, Natty Narwhal, On an Intel Atom duel core (net-top).

---

