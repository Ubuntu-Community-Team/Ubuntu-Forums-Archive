---
title: "Running x11/nodejs standalone"
date: 2012-01-05
forum: General Help
---

### Post by mo_wmw on 2012-01-05
I'm currently developing on a automated info-system which is based on a self-written nodejs-service which is also starting a firefox instance. This system should run in ubuntu without any controlling of anyone.

My current problems are lying in the autostart of the xServer and our own Service. I created init.d-scripts which are working and linked in the rc-folders bei rc-update defaults etc.

(Xserver is started by startx in init.d-script)

The xServer is shutting down when reaching the login-screen of debian (without any gui) and the firefox in our service is reporting that it couldn't reach the display.

Sometines the xServer keeps running but there is no chance reaching it by programs with gui.

Is there a chance to run these setup?

Greetings and a happy new year,

Moritz

---

