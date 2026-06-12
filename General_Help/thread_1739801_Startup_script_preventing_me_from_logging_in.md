---
title: "Startup script preventing me from logging in"
date: 2011-04-26
forum: General Help
---

### Post by laredotornado on 2011-04-26
Hi,

I'm using Ubuntu 10.  I want to run a selenium server (Java process) on system startup, however in my startup script, I forgot to run the process in the background (didn't add a "&" to the end of the server startup invocation).  Now when I reboot my system, it just sits there, without producing the screen to be able to login.  Additionally, I can't remote login through SSH.

Any ideas how I can get into the system?  Thanks, - Dave

---

### Post by tredegar on 2011-04-26
Boot from a live CD
Mount your HDD filesystem somewhere.
Fix up the broken script. 
Shutdown. Remove CD. Reboot.

---

