---
title: "Folding@Home fails to load."
date: 2010-01-16
forum: General Help
---

### Post by AndrewCrogonk on 2010-01-16
When I got this message I thought the thing was already installed despite the failure of a startup script.
> andrew@ubuntu:~$ sudo origami install -t 45104 -u AndrewCrogonk -b big
INSTALLING... PLEASE BE PATIENT
ERROR: STARTUP SCRIPT FAILED TO START!


So I tried to run "sudo origami start" and I get this.

> andrew@ubuntu:~$ sudo origami start
starting origami...
andrew@ubuntu:~$ 
['folding' ver. 6.2]

Starting up FAH client(s) on 2 processor(s):
Starting FAH client at CPU1...
FAH client #1 startup: OK 
Starting FAH client at CPU2...
FAH client #2 startup: OK 


Starting of FAH client(s): FAILURE 


Can anyone help?

---

### Post by secondstage on 2010-06-07
See if either of these solutions work for you.

[https://bugs.launchpad.net/origami/+bug/372114/comments/4](https://bugs.launchpad.net/origami/+bug/372114/comments/4)

[https://bugs.launchpad.net/origami/+bug/297578](https://bugs.launchpad.net/origami/+bug/297578)

Good luck.

---

