---
title: "Workaround for running Wine programs on Ubuntu Server?"
date: 2012-07-10
forum: General Help
---

### Post by TheTwitch on 2012-07-10
Hi there

I have set up an ubuntu server to run CoD servers. I have a script which lets me give a whole bunch of parameters / etc and start the server to that configuration.

As the CoD server requires a window, I installed xrdp and fluxbox for running them.

Currently the way the script works is that I have a screen terminal open on a xrdp session. I store the name of the screen window in the script, and when I want to start / stop a server, commands are sent to that window, which opens it in the xrdp session. This works perfectly fine (and I think is pretty cool too), but has some problems...

Firstly, the xrdp session is not persistent (I can't access it by using RDP on any computer, only the one I started the session from).

Secondly, the xrdp session does not start when the Ubuntu server starts, so I have to go and start a session when the server starts, so the script can run.


What workarounds are there for this problem? Should I even bother using xrdp, or is there something better?

Cheers

---

