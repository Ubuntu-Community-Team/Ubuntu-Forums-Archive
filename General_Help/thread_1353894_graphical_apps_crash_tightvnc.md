---
title: "graphical apps crash tightvnc"
date: 2009-12-13
forum: General Help
---

### Post by CharlesA on 2009-12-13
Hi all,

I've got Ubuntu 9.04 installed and I am using VNC tunneled over SSH if I need to access the desktop.

Anyway, sometimes, when I launch an application, it'll crash the vncserver. To get it back up and running I need to remove two files:

```
sudo rm /tmp/.X60-lock
sudo rm /tmp/.X11-unix/X60

```

I don't know if it's the version of tightvncserver that I am running that's causing the problem, or if it's something else.

Any help would be appreciated.

Thanks.

---

### Post by CharlesA on 2009-12-14
Any ideas on this? I can't be the only one having problems.

Still not solved, but since I've redone my server to terminal only, it won't be a problem any more.

---

### Post by twignation on 2011-07-19
Ah, I see that you have not solved this problem, but moved into another place [http://ubuntuforums.org/showthread.php?t=1285668](http://ubuntuforums.org/showthread.php?t=1285668)

I have the exact same problem, so I would love to see a solution. I have had this set up before and not had this problem.

Also, this happens regardless of what machine or system I use to remote into the server with..

---

### Post by twignation on 2011-07-19
not sure if this is any help, but a dmesg | tail returns with this:


Xtightvnc[4693]: segfault at 7fffaf61c000 ip 000000000044e4f1 sp 00007fffaf61aa60 error 6 in Xtightvnc[400000+17e000]

---

### Post by twignation on 2011-07-19
> **twignation said:**
> not sure if this is any help, but a dmesg | tail returns with this:


Xtightvnc[4693]: segfault at 7fffaf61c000 ip 000000000044e4f1 sp 00007fffaf61aa60 error 6 in Xtightvnc[400000+17e000]


I hope this is useful to the next reader: I am running a 64bit server, so I assume that this problem is in fact being discussed here:

[http://ubuntuforums.org/showthread.php?t=1396744](http://ubuntuforums.org/showthread.php?t=1396744)

---

