---
title: "Crontab script to restart crashed Opensim region"
date: 2011-11-10
forum: General Help
---

### Post by Lee1275 on 2011-11-10
Hi, I run 4 regions on OSGrid on a dedicated Ubuntu 10.04 server.  Like all programs the regions instance sometimes crashes.  What I would like is help in writing a script using crontrab (or similar)  that will check every 5 minutes to see if a Screen named OSGrid.**** is running.  If it is, then do nothing and wait 5 minutes then check again.  If it no screen with OSGrid in the name can be found it will run the opensim start script which is ./Osgrid.sh


I don't know too much about scripting, so any help would be gratefully received.  I don't want anything fancy, just a simple crontab that will check the screen is running every 5 minutes.

Thanks in advance.

Lee

---

