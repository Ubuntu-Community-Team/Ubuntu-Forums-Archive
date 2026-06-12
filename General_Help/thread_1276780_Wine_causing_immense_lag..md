---
title: "Wine causing immense lag."
date: 2009-09-27
forum: General Help
---

### Post by 90sgamer on 2009-09-27
I have a 2.4 GHz quadcore, 3G of RAM, and a Radeon HD4850, but Starcraft (since uninstalled), for example, runs so slowly that I can see images load from top to bottom over a period of several seconds.

When I exit the program, the lag continues.  GNOME takes a couple of seconds to change my cursor when I move between a terminal and the desktop.  It also takes seconds to highlight a button or icon when it should and to load a menu.

The other 1/4 of the time, Wine works perfectly for my needs (10+ year old games, emulators, etc.).

The only thing I can do is to log out and log back in, ending this lag, then to retry running it.  Any other solutions?

---

### Post by lovinglinux on 2009-09-27
I had this problem a while ago with a game in wine. The problem was the PunkBuster service, used to block cheaters. PunkBuster starts every time the game is started, but it doesn't shut down with the game, since it is a service. So, PunkBuster can slow you down even after the game is closed. To solve this, open the System Monitor and kill all wine related stuff. I don't remember exactly, but there is a services.exe or something like that.

---

