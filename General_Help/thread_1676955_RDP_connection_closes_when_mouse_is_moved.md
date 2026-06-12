---
title: "RDP connection closes when mouse is moved"
date: 2011-01-28
forum: General Help
---

### Post by styne on 2011-01-28
Hi,

I'm using Ubuntu 10.10 and I have setup vino, tightvncserver, and xrdp so that I can connect from a Windows machine.

I can connect successfully from Windows using sesman-xvnc and I get the unlock dialogue but as soon as the mouse is moved then it quits with no error message.

I was monitoring my Ubuntu machine while this occurred and as soon as the mouse was moved, all 4 CPUs went up to 100%. I repeated and next time only 2 CPUs went to 100%. The 2 processes that were using all this processing power were ubuntu-sso-login and mission-control-5.

Does anyone know a) why it quits when the mouse is moved, and b) why it causes at least 2 CPUs to run at 100%?


Thanks

---

