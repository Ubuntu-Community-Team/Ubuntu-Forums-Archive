---
title: "running an app without login"
date: 2010-04-21
forum: General Help
---

### Post by Jethro_uk on 2010-04-21
I have a ubuntu 9.10 machine which is left 24/76, as my "download server". I have Vuze/Azureus installed, which I control mainly through the HTML UI, so rarely log into the machine.

Currently, when the machine restarts (not often) I have to log in via NeatX, and run Vuze. I then disconnect, and use the HTML UI.

Is it possible to set Vuze to run automatically, on startup, without the neeed to log in ? If I did this, where exactly would it be running ? As what user ? And what would happen if I then logged in, and ran it in a session ?

---

### Post by P4man on 2010-04-21
ha, im in a very similar situation. You can have ubuntu login automatically of course, and run your BT client automatically on boot (system > preferences > startup applications) but then if you log in using QTNx (which is what I use, i think its like NeatX) you wont have access to the session in which your BT client runs, as it creates a new session.
Kind of annoying.

---

### Post by Jethro_uk on 2010-10-12
Having run Vuze for a few months now, it seems massively overbloated for what I need. Also I suspect it's developed a resource leak, as I find my machine needed rebooting after a few days leaving Vuze running.

Have switched to using TorrentFlux, which is exactly what I wanted: A torrent client that can be controlled over the internet, and which can run without a gui session being started.

---

