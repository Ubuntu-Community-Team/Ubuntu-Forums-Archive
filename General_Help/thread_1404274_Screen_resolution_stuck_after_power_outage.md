---
title: "Screen resolution stuck after power outage"
date: 2010-02-11
forum: General Help
---

### Post by VTBuc on 2010-02-11
So yesterday, I my power went out on my desktop and when I rebooted, the screen resolution was stuck at 640x480. When I go to the display settings, no other higher options are available. Any suggestions?

---

### Post by 3Miro on 2010-02-11
Try System -> Admin -> Hardware Manager and make sure some driver did not get messed up or something.

You can also try to reconfigure the x-server. Look at this:

[http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/](http://www.cyberciti.biz/faq/ubuntu-linux-how-to-reconfigure-x-windows-system-xorg-server/)

The command is basically:
```
sudo dpkg-reconfigure xserver-xorg
```

---

