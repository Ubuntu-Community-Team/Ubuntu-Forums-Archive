---
title: "new kernel, no irc"
date: 2006-04-06
forum: General Help
---

### Post by Vege on 2006-04-06
Hi
This sounds funny, but when i updated my kernel to 2.6.17-rc1 from 2.6.10 as it included a driver for my wireless network, all went well and kernel is working, but when i start any IRC client available (Konversation/Irssi/X-Chat) it hangs like so:

[15:30] [Info] Looking for server irc.freenode.net:6667...
[15:30] [Info] Server found, connecting...
[15:30] [Info] Connected; logging in...
[15:30] [Notice] -- *** Looking up your hostname...
[15:30] [Notice] -- *** Found your hostname, welcome back
[15:30] [Notice] -- *** Checking ident
[15:31] [Notice] -- *** No identd (auth) response

thats the last line that pops up.

All other internet services work fine.
In old kernel 2.6.10 everything is working right.
So i blame the Kernel, anyone has a solution?

---

### Post by z-vet on 2006-04-08
Some servers don't allow you to connect if you have no identd (auth) - service that responds to authentication request from irc server. You need to install one. The simplest way (for me) was to install [fakeidentd](http://hangout.de/fakeidentd/). There's no package available, get the source and compile it, it's very quick and easy. Read an "INSTALL" file, it contains all info you need. 
PS: sorry, i don't know how this problem is related to your kernel upgrade.

---

### Post by thomashauk on 2006-04-08
Try oidentd because that is in the repositories.

---

