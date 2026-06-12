---
title: "Byobu as default inLXTerminal/Lubuntu"
date: 2010-12-02
forum: General Help
---

### Post by ElNerdoDeGeek on 2010-12-02
Hey all,

I'm running a small server on a Lubuntu install, and I'd like to have new terminals start in Byobu, or at least screen. However, I can't figure out how to make Byobu start automatically. The built-in "Start Byobu with login" option doesn't seem to do anything, although it does add a line to my ~/.profile. How can I set Byobu as my default shell?

--Matt

---

### Post by Baneblade on 2011-01-04
Hi Matt,

You need to make sure that you are running the command as a login shell for byobu to start automatically when you launch your terminal.

I'm not sure about Lubuntu, but on Ubuntu it's found in:

Edit -> Profile Perferences -> Title and Command

Hope that helps?

---

