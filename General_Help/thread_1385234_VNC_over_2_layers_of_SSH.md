---
title: "VNC over 2 layers of SSH"
date: 2010-01-19
forum: General Help
---

### Post by dr_latino999 on 2010-01-19
I've got the OK from my manager to set this up, so I just need a little help. I've seen the tutorials on setting up VNC over SSH which works all fine and dandy, but I need access to my work PC when I'm not on the University Network. To log in to the command line I would have to ssh from putty to a central box that is visible to the outside network (i.e. the world) and from that box, I would have to ssh into my workstation.

Logical flow:
SSH-Putty --> SSH-Midddleman --> Desktop-command line

How would I setup VNC to deal with the middleman?

---

### Post by Brandon Williams on 2010-01-19
I do the same thing for VNC into my office workstation.

First, open a tunnel through the external gateway to ssh into your internal host.
```
ssh -N -L2222:your.host:22 external.gateway
```

Second, open a tunnel for VNC that goes through the first tunnel.
```
ssh -N -L5901:localhost:5901 -p2222 localhost
```

Now, you can start the VNC viewer through the inner tunnel.

---

