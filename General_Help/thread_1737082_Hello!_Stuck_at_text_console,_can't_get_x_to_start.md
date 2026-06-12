---
title: "Hello! Stuck at text console, can't get x to start!"
date: 2011-04-23
forum: General Help
---

### Post by marblecatdog on 2011-04-23
Ok, so I tried restarting the x server with alt ctrl backspace and now I'm stuck at a text console!  I've tried rebooting but it just brings me back to the text console, how can I get x server back??

---

### Post by marblecatdog on 2011-04-23
I've tried using startx and initx but it gives me an error, unable to connect to x server

---

### Post by thehipho on 2011-04-23
Delete your xorg.conf if not set right it could cause problems?


```
sudo rm -f /etc/X11/xorg.conf
```

Reboot.

---

### Post by marblecatdog on 2011-04-23
Ok, that worked.  Any idea what caused that?  I've restarted x server tons of times before, I'm a little worried to do it again now...

---

### Post by thehipho on 2011-04-23
Glad to hear it worked for you.
Just don't know what caused that? something was upgraded?
I guess, We learn along the way dealing with unwanted errors?

---

### Post by fdrake on 2011-04-23
check your xsession errors log if you did something wrong:

gedit /home/username/.xsession-errors.old

---

### Post by thehipho on 2011-04-23
Also look for NVIDIA errors in:
 /var/log/Xorg.0.log   &  /var/log/Xorg.0.log.old

Bye.

---

