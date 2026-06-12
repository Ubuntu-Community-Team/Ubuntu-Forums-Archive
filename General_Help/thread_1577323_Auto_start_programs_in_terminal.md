---
title: "Auto start programs in terminal"
date: 2010-09-18
forum: General Help
---

### Post by Qwertinsky on 2010-09-18
I am setting up a streaming audio server. I would like to have Darkice and sc_serv (Shoutcast server) start automagically on boot. 

I have set Xubuntu (10.04) to auto login 

Both Darkice and sc_serv are command line apps and I would like them to each run in their own terminal window so I can monitor any status messages they produce. For instance sc_serv displays connections disconnections with time connected, and current number of listeners, and I want to see that. 

One important note: sc_serv must be up and running before Darkice can be started.

---

### Post by bodhi.zazen on 2010-09-18
I suggest you run this in screen sessions.

Tons of tutorials on screen (screen is in the Ubuntu repos)

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

IMO it is easiest to then call the apps from /etc/rc.local, but you can write init scripts if you prefer.

You may also need to add a few sleep in /etc/rc.local as rc.local may run before the system is fully booted (due to concurrency).

---

