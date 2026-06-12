---
title: "vnc4server controlled session on Lubuntu (LXDE)"
date: 2012-01-30
forum: General Help
---

### Post by manox on 2012-01-30
Hi I have lubuntu installed on my HTPC which I wont to control from other computers. So I have installed vnc4server where my ~/vnc/xstartup is 
```
   #!/bin/sh
    export XKL_XMODMAP_DISABLE=1
exec ck-launch-session startlxde & vncconfig -nowin

```
I wont to connect to current sesion and control my HTPC

---

