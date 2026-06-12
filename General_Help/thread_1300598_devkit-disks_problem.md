---
title: "devkit-disks problem"
date: 2009-10-25
forum: General Help
---

### Post by Pitboss on 2009-10-25
Hi, does anybody has a solution for the following situation:

in Karmic in order to mount a particular partition of my hard, I need to authenticate it every time i mount it. How can I make that it devkit-disks doesn't need my password every time.

EDIT: sorry for bothering you, I found the solution:

man PolicyKit.conf, edit the /usr/share/polkit-1/actions/ files.

---

