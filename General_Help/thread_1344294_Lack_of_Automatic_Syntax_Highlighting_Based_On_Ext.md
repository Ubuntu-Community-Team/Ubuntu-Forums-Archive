---
title: "Lack of Automatic Syntax Highlighting Based On Extension in Gedit Upon Opening Files"
date: 2009-12-02
forum: General Help
---

### Post by partymetroid on 2009-12-02
Hey, guys.  If I recall correctly, Gedit used to automatically highlight a file based on syntax **upon opening a file**.  If it had done it before, then it no longer does it anymore.

Anyway to get Gedit to automatically highlight based on syntax **upon opening a file**?

---

### Post by partymetroid on 2009-12-02
I resolved the issue! :)

A kind fellow on the irc.gnome.org #gnome channel gave me a gconftool-2 command for reconfiguring Gedit:
gconftool-2 --type bool  --set /apps/gedit-2/preferences/syntax_highlighting/enable true.

Hope this is somehow helpful to anyone who has/will have this problem. :X

Cheers! :D

[edit] Scratch that.  It apparently only won't work with Ruby, erb, and other Ruby on Rails-associated files I've been using.  XML, HTML, etc. seem to work just fine.

:(

---

