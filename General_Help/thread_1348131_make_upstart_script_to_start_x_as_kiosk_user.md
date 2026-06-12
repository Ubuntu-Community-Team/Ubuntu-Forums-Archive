---
title: "make upstart script to start x as kiosk user"
date: 2009-12-06
forum: General Help
---

### Post by Robvdl on 2009-12-06
Currently I am running an Adobe Air app on a mini ITX machine, which is running a minimal install of ubuntu server 9.10.  I've installed xorg and openbox (I want this to be very lightweight).  I have created a kiosk user and a custom .xinitrc for that user, that starts both openbox and the air application, it also makes sure the air application restarts when it is terminated (or crashes).  Currently I start X by autologging the kiosk user into tty1 at boot, and starting x from the .bashrc file for the kiosk user, but that is a bit hacky.

I want to covert all this to an upstart script to start x instead.  This upstart script should preferably start x as the kiosk user, not root, and autologin.  I should be able to stop and start the service.

I know upstart configuration files are in /etc/init, and I have created a simple upstart script that runs startx as root, however this is not what I want, and I cannot seem to stop the service anyway.

Any help with this would be appreciated.

---

