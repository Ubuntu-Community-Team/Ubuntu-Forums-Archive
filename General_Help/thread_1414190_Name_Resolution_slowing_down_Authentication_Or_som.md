---
title: "Name Resolution slowing down Authentication? Or something else?"
date: 2010-02-23
forum: General Help
---

### Post by krimzen85 on 2010-02-23
Hi All,

As mentioned in another of my recent posts, I have set up a small network for my job, in which I am utilizing 4 Servers running Ubuntu 9.04 Jaunty Jackalope Gnome GUI and Ubuntu Server running underneath (yes I need a GUI for what I am doing).

However, I am having a problem when bringing Ubuntu out of "locked" state, and any time that I am required to authenticate (i.e. sudo bash). After I type in my password, everything hangs for a good 3+ minutes.

To test this, I disconnected the Ubuntu Servers from the network, and I tried to authenticate again. With the server off the network, authentication did not hang, and the GUI came up in seconds. Also, I checked my syslog and memory utilization and both are well within acceptable range that they would not be causing sluggish performance.

With all of this said, I believe that there is some kind of resolution going on when trying to authenticate while the servers are connected to the network (i.e. Kind of like how doing a traceroute in a cmd prompt in Windows without the "-d" takes forever because of name resolution checking).

I should also mention that my network DOES NOT have an internet connection by design.

Does anyone have any solutions to this problem?

---

