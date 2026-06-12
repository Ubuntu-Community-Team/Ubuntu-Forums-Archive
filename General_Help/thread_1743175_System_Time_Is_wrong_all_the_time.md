---
title: "System Time Is wrong all the time"
date: 2011-04-29
forum: General Help
---

### Post by gauth91 on 2011-04-29
Hai folks!I installed Ubuntu inside windows(Win 7).Both works good.I found that system time is wrong in both OS.Every time i Change it manually but it changes again on reboot!Help me out

---

### Post by kleskjr on 2011-04-29
Go to Administration menu and find 'Time and Date there'
By clicking on the lock you can unlock and select online synchronization with online time servers. wish you luck.

and I guess that the time is not correct in both OSes because u run out of batteries ;)
There is a small battery on the motherboard which probably wants to get retired.

---

### Post by cavalier911 on 2011-04-29
Windows sets hardware clock and software clock to local time.
Lubuntu sets hardware clock UTC with an offset TZ to adjust software clock to local time.

Configure Lubuntu to use localtime:
```
sudo leafpad /etc/default/rcS
```
UTC=no
Save

---

### Post by KegHead on 2011-04-29
Hi!

It could be your mobo.

Have you checked for any bios updates?

KegHead

---

