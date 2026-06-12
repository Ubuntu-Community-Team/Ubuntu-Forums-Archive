---
title: "Emulate display in Xubuntu for VNC"
date: 2011-01-18
forum: General Help
---

### Post by jim2013 on 2011-01-18
I have a Xubuntu box that I use as a server (Apache2, FTP, etc.) that I  have used xfce to set up. I currently have the box in a headless setup. I  access the box both by SSH and VNC. When I boot the box with a display  plugged in, Xubuntu automaticly logs in as my main account and boots  properly. When I do not have a display hooked up on startup, the box  auto logs in, but fails to start an X session. What I would like to do  is to start a X session on system startup automatically. I have seen a  tutorial on how to fool X into thinking there is a display attached by  modifying xorg.conf, but the tutorial doesn't work for me. I need to be  able to VNC into a full xfce session and have the session be persistent.  I want to be able to have the server emulate a display so that X is  started on that display. I then want to be able to VNC into that display  for a persistent VNC session. I have seen this done as an example but I  cannot figure out how to do it. 
Thanks,
Jim2013

---

