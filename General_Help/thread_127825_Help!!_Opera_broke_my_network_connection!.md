---
title: "Help!! Opera broke my network connection!"
date: 2006-02-09
forum: General Help
---

### Post by MagisterJoe on 2006-02-09
Or something like that.

I'm in WinXP now (see, THIS is why I don't delete it...otherwise I'd have to go to the library to get internet access when I mess something up ^_^).  I installed opera from the multiverse through synaptic.  I got the "unverified" or whatever word (I'm a little fuzzy) warning, but I ignored it, because it's Opera! (hindsight says DUMB!!).

So, I install Opera open it up, and ssh2 to my server to do some file editing.  After about five minutes, the session freezes and all network traffic stops (wireless using madwifi).  I plug into the router, disable ath0, enable eth0, and try to ping anything...

I get: 

ping sendmsg: operation not permitted.

Same when I reboot.  I got a network connection for about five minutes, then nothing.  Same result several times.  Haven't uninstalled opera yet, wanted to see if there might just be some setting that I can mess with.

HELP!

---

### Post by z_diver on 2006-02-10
You should be able to get your connection back by typing '/etc/init.d/networking restart' in a terminal window.  That's certainly not the answer but it's easier than rebooting.;)

---

### Post by nanotube on 2006-02-10
does the error happen even when you dont have opera open?

---

### Post by MagisterJoe on 2006-02-10
Well, after rebooting out of windows, network came back up, worked fine for about 20 minutes using firefox, ssh, etc...then i ran with opera open for about five minutes before I had to go to work.  Seemed to work fine.  I still haven't retried the deadly Opera + ssh combo yet.

---

