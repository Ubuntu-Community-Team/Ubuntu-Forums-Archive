---
title: "Problem with inetd ( xinetd)"
date: 2010-06-12
forum: General Help
---

### Post by hung3nguyen on 2010-06-12
I'm reading some papers about using inet , xinetd. Those papers say " UNIX and UNIX-like systems provide a program called inetd or xinetd ". I found both inet, xinetd but there's nothing about inet or xinetd in my Ubuntu . That's very weird. Can someone explain to me and help me use inetd or xinetd program.
Any help will be appreciated.

---

### Post by gzarkadas on 2010-06-13
Open a terminal window (menu Applications|Accessories|Terminal) and type inside:
```
man inetd
``` This will bring documentation for the program. 

In general you do not need to do anything with it; it is a deamon and is active by default. Only if you want to setup a network service, or tweak an existing one you might have to edit its configuration file, /etc/inetd.conf.

---

### Post by gmargo on 2010-06-13
There are several choices for an "inet-superserver" on Ubuntu, none of which are installed by default (except perhaps on a server install?):
```

$ apt-cache search inet-superserver
openbsd-inetd - The OpenBSD Internet Superserver
xinetd - replacement for inetd with many enhancements
inetutils-inetd - internet super server
rlinetd - gruesomely over-featured inetd replacement

```I recommend installing the **openbsd-inetd** package.

---

