---
title: "Tomboy --quiet;  Question"
date: 2010-12-07
forum: General Help
---

### Post by oaxacamatt1 on 2010-12-07
Hey All,
I have a question for Tomboy.  

I have been starting it up by using the Startup Application panel.  I added it to the menu of items then added the command/option '--quiet'. I thought I had read that this would start tomboy and keep it from opening up the 'search window' or the 'start here' windows but alas no...

Does anybody know how to keep Tomboy quiet or silent and keep it from opening ANY windows on my desktop?
It's really bothersome,
M

---

### Post by sharm on 2010-12-08
Tomboy does not have a --quiet option, contrary to some mistaken advice I've seen in the Ubuntu forms and AskUbuntu.

We could add such an option (please file an upstream bug if you like), but in theory Tomboy only shows the Search window if you do one of these things:

1) Start Tomboy with -search (which is what the default application menu item does)
2) Start Tomboy when it's already running
or 3) Start Tomboy without a notification area

The most common problem I see is people accidentally starting Tomboy twice.

---

