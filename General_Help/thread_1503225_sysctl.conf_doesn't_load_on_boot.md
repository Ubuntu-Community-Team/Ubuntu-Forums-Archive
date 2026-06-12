---
title: "sysctl.conf doesn't load on boot"
date: 2010-06-06
forum: General Help
---

### Post by srivo on 2010-06-06
I made some change to my sysctl.conf file and it they doesn't seem to load at boot? Each time I boot I need to send a sudo sysctl -p command to load the new parameter!

Is it normal?

---

### Post by srivo on 2010-12-07
It's a bug! 

See: [http://bugs.launchpad.net/ubuntu/+source/procps/+bug/50093](http://bugs.launchpad.net/ubuntu/+source/procps/+bug/50093)

---

