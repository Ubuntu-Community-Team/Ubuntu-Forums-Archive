---
title: "Simple Network Monitor"
date: 2006-03-31
forum: General Help
---

### Post by Cursor on 2006-03-31
New to this forum, fairly new to Linux, been using Ubuntu for about a month now.  Works great for everything I need, except for one thing...
I would like to set up a network monitor for some of my clients.  Nothing complicated, just ping checks really.  I need to know only two things; if the client's router (usually a D-Link home router) is up, and it's latency from my machine.
I have played around with a couple tools, munin, smokeping, etc... with little success.  ](*,) 
I'm looking for recommendations on a decent ping monitor, preferably something that displays the information on a web page so I can check on it from away from the office.
Any ideas?

Ryan

---

### Post by KingBahamut on 2006-03-31
I wrote a backended php script for my website  that does what your talking about for my customers. If your looking for something more functional than that, then you can try nagios ([http://www.nagios.org/](http://www.nagios.org/)) , apt-get install nagios-mysql for the installation.

---

