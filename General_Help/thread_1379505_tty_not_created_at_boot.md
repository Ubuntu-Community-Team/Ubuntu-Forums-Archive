---
title: "tty not created at boot"
date: 2010-01-12
forum: General Help
---

### Post by berale on 2010-01-12
Hi,
On 9.10, probably after updating, tty consoles are not created during boot. When using Ctrl+Alt+F[1-6] I get a blinking cursor and no login prompt. 
When I use:
```
sudo getty -8 38400 tty1
```
a tty port is created and I get the login prompt.

Any ideas on how to get it back to normal?

---

### Post by mörgæs on 2010-01-13
There is another thread regarding tty, but it is mostly about shutting down:
[http://ubuntuforums.org/showthread.php?t=1379358](http://ubuntuforums.org/showthread.php?t=1379358)

In that I pointed to Launchpad. Does your problem fit the description there?

---

