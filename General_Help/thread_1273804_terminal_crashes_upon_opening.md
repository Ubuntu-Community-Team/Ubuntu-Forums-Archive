---
title: "terminal crashes upon opening"
date: 2009-09-23
forum: General Help
---

### Post by blue_flame on 2009-09-23
I have Ubuntu 9.04 (Jaunty).

I edited a terminal profile to start up with the command, "/bin/sh | cd Desktop". I was just messing around with what commands I could enter. Before I restarted terminal I noticed that the default shell is /bin/bash, but re-opened terminal anyway.

I understand why it crashes, but I don't understand why I can't fix it.
(it executes /bin/sh with the pipe operator which tells it to execute cd Desktop with /bin/sh)

I tried using "gnome-terminal --window-with-profile=default" to open the default profile, but that doesn't work.
I went into the "/home/user/.gconf/apps/gnome-terminal/profiles/Profile0" folder and edited the "%gconf.xml" file to match the "/home/user/.gconf/apps/gnome-terminal/profiles/Default/%gconf.xml" file.
I tried cold and warm booting, and I tried to open the terminal each time..

I searched google and I couldn't find anything.

I can access root terminal, but it doesn't let me change the profiles of the gnome-terminal.
I'm totally lost.
Help.
:confused:

---

