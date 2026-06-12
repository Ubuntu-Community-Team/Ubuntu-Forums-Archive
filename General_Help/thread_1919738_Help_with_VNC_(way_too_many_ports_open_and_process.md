---
title: "Help with VNC (way too many ports open and processes running)"
date: 2012-02-03
forum: General Help
---

### Post by jimgwilliam on 2012-02-03
Hi Folks,

Looking for a little help here.  I have an ubuntu laptop that I leave at school which I want to remotely connect to through ssh/vnc from another ubuntu laptop at my home.

I'm actually successfully able to do this now, having set up vnc and ssh servers at the remote site and then using the client side from home.

The script I'm using to connect to the remote machine is

```
 #!/bin/sh

ssh -f -L 5900:localhost:5900 user@hostname \
        x11vnc -safer -localhost -nopw -nevershared -forever -display :0 \
        && sleep 5 \
        && vncviewer localhost:0 
```

except I have my own laptop name filled in for user@host.  

I actually can connect this way and it works fine, but when I close the VNC window after a session, the process stays active, such that the next time I try it, it says I'm running on VNC Desktop :2 .... then :3 .... then :4, etc.

When I look at the processes running using "top" on the remote side, I have almost 18 processes called "x11vnc".  How do I make sure that every time I connect to the remote machine it doesn't start another x11vnc process in my list and increase the port number from 5900 to 5901, 5902, 5903, etc.  I'm up to 5918 now.

Any help would be appreciated.


Thanks,
Jim

---

