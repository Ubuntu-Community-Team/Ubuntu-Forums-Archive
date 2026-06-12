---
title: "g15 daemon/macro problems"
date: 2009-11-25
forum: General Help
---

### Post by TheLazyGenius on 2009-11-25
i don't know if this is normal. it always will say there is an error when i install a program with these two things....

example:
Setting up g15daemon (1.9.5.3-3) ...
Starting g15daemon: invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of g15macro:
 g15macro depends on g15daemon; however:
  Package g15daemon is not configured yet.
dpkg: error processing g15macro (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 g15daemon
 g15macro
E: Sub-process /usr/bin/dpkg returned an error code (1)




now these programs still work, sometimes, fine. sometimes, i feel like i'm missing something... Is this normal or should i worry about it?

edit:

like this since i started.....
from ubuntu 8.04

---

