---
title: "Launch sudo script at startup on Ubuntu 11.10 Unity"
date: 2011-11-16
forum: General Help
---

### Post by jBriche on 2011-11-16
Hello,
I recently migrated from ubuntu 10.10 to Ubuntu 11.10  with Unity.
I had a script that was launched at startup using rc.local (in /etc/..). That script needed to be launched as root without asking any password.

I tried to do the same in Ubuntu 11 bt it didn't work.
The same rc.local file doesn't launch my script.
I tried to use xdg and put a new job to be launched (tried both in ~/.config/autostart or in /etc/xdg/autostart) and it always ask for my password instead of direclty launching as root.
Is there a way to launch a root script at startup, if yes which one it is?
Of course I already tried to google my question but almost every post is about previous version of ubuntu

Thanks in advance
Julien

---

### Post by raja.genupula on 2011-11-16
[http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/](http://www.aoddy.com/2009/03/02/how-to-start-a-script-by-root-permission-at-boot-time-on-ubuntu-server-810/)

EDIT got one more thing : [http://www.tuxation.com/setuid-on-shell-scripts.html](http://www.tuxation.com/setuid-on-shell-scripts.html)

all the best.

---

### Post by prodigy_ on 2011-11-16
**rc.local** does work as usual in 11.10. Need to see that script of yours to figure out what's wrong with it.

---

### Post by jBriche on 2011-11-16
Thanks for your answers but I finally found the bug I had (why my rc.local didn't work), the file had wrong permission...
Two days I was on it...

But thanks for the tip raja I never thought about that, it might be usefull some other day.

---

