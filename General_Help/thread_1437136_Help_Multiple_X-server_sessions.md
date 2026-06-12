---
title: "Help: Multiple X-server sessions"
date: 2010-03-23
forum: General Help
---

### Post by caanderson555 on 2010-03-23
I posted yesterday regarding this problem, and seemed to have worked around it (not a permanent solution though).  

Running Lucid Beta release on a Thinkpad T410.  (since Karmic would not install  on this machine correctly)

I am unable to login at the login screen, so switch to the command line and login.  From there, startx will always yield an error, telling me to remove the file /tmp/.X0-lock.  Even after doing so, startx gives the error: cannot establish any listening sockets.  The only way around this is to start a new x-session using startx -- :1.  This boots up no problem and reliably.

I can do this everytime I login (not too much extra work, but annoying,  probably slowing down the computer), and am hoping to find away around it. 

 Any thoughts?  Not sure if this is a bug getting worked out still or what with the new release.

Thanks to all

Casey

PS. have tried dpkg-reconfigure xserver-xorg, which does not do anything.

---

