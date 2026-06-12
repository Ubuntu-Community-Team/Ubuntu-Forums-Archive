---
title: "How to make /etc/init.d scripts start on boot?"
date: 2010-04-23
forum: General Help
---

### Post by andrewdied on 2010-04-23
I have a script (/etc/init.d/pcscd) that used to start on boot, but no longer does.  What do I need to edit or run to make it start on boot again?  

As far as I can tell it should be already working.  In the header of the script it says to start on almost all runlevels
```
# Default-Start:     2 3 4 5
```

and I'm in runlevel 2:
```
andrew@bun-bun:~$ runlevel
N 2
```

I'm currently running Ubuntu 9.10.  Thanks for the help.

---

### Post by iponeverything on 2010-04-23
[https://bugs.launchpad.net/ubuntu/+source/pcsc-lite/+bug/506908](https://bugs.launchpad.net/ubuntu/+source/pcsc-lite/+bug/506908)

---

