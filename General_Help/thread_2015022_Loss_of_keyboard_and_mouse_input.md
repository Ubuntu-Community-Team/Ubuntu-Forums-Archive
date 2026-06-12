---
title: "Loss of keyboard and mouse input"
date: 2012-07-02
forum: General Help
---

### Post by billcauley on 2012-07-02
While using Thunderbird to read newsfeeds this time, all input devices failed... no mouse or keyboard, except that the keyboard took Ctrl-Alt-Del which produced a logout menu.  Logged out and then in, and the devices are now working.  Wonder what's happening?

12.04 Gnome Classic (no effects)

---

### Post by stderr on 2012-07-02
It mightn't be awfully easy to work out what happened. Your best hope is that there are some pertinent log entries which give some indication what happened. 

Check /var/log/syslog and /var/log/messages around the time it occurred - see if there's anything interesting.

It sounds as though the xserver was still alive since you got a logout window.
It might be that some component of the DE crashed. Or it may be that a USB mouse was force disconnected. Hopefully the logs might give a clue.

---

### Post by billcauley on 2012-07-03
Thank you, I'll give it a look!

---

