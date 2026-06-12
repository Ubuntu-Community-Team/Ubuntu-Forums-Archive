---
title: "Ping plotter for Linux"
date: 2010-11-01
forum: General Help
---

### Post by Blinkiz on 2010-11-01
**I need to find a ping plotter that can ping each hop in a traceroute and present it in a diagram.**

In the Windows world, it exist a excellent program called [PingPlotter PRO]("http://www.pingplotter.com/").
[IMG]http://www.pingplotter.com/nessoftgraph.gif[/IMG]


[LIST]
[*]Sure, more advanced solutions is also welcome. As long as it get's into a RRD file or similar, am happy.
[*]Each hop along a traceroute needs to be checked ~0.5 second.
[*]Am also open for programs that are not Open Source. Even needed to pay for as long as it's not to expensive.
[/LIST]

---

### Post by a-user on 2010-11-01
i used "traceroute" for such things. it is a command line tool. dont know if there are graphical frontends to it or other programms like that. but it should be easy to formate its out put the way you want and make a graphical representation of it.

---

### Post by Blinkiz on 2010-11-01
> **a-user said:**
> i used "traceroute" for such things. it is a command line tool. dont know if there are graphical frontends to it or other programms like that. but it should be easy to formate its out put the way you want and make a graphical representation of it.
Hmm.. I do not really know how to respond to this...
I work professional as a computer engineer and have used debian/ubuntu for a couple of years now.

---

### Post by matt_symes on 2010-11-01
Hi

Maybe this thread will help

[http://ubuntuforums.org/showthread.php?t=696513](http://ubuntuforums.org/showthread.php?t=696513)

What about ping plotter under wine?

Kind regards

---

### Post by Blinkiz on 2010-11-01
> **matt_symes said:**
> Hi
Maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=696513](http://ubuntuforums.org/showthread.php?t=696513)
What about ping plotter under wine?
Kind regards
Thanks for the response Matt.
On the link you provided, SICM and M-Ping is suggested. M-Ping can not plot a traceroute path more than one time. SICM does not seem to be able to do this at all.

Under wine. Well.. Hmm.. Maybe it's possible. But I think the Linux world must have something similar :)
**Am looking for a tool that can measure packet drops along a traceroute path.** I should probably have described this in my first post.

---

### Post by Blinkiz on 2010-12-15
Thanks to the user rww in ubuntu channel on freenode, the perfect tool for this is "mtr". It's included in ubuntu as default. The GTK version is no good, so make sure to use curses version.

---

### Post by Blinkiz on 2011-12-25
Just want to update this thread and say that mtr is great!

---

