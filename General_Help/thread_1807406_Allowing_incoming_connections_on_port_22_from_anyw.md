---
title: "Allowing incoming connections on port 22 from anywhere"
date: 2011-07-19
forum: General Help
---

### Post by emurad on 2011-07-19
Hello,

I'm trying to get VNC working but I'm getting this error message:

> ssh: connect to host my_ip_address port 22: Connection refusedWhen typing:

> ssh -f -L 5900:localhost:5900 user@my_ip_address x11vnc -safer -localhost -nopw -once -display :0 && sleep 5 && vncviewer localhost:0I'm trying to follow the instructions here: [https://help.ubuntu.com/community/VNC#Guide%20to%20example%20scenarios](https://help.ubuntu.com/community/VNC#Guide%20to%20example%20scenarios) but I'm struggling with point 2 & 3:

> 2. If you have previously reconfigured the firewall on your PC, make sure the firewall allows incoming connections on port 22 from anywhere, and on port 5900 from localhost (also known as 127.0.0.1) 

3. If your PC is behind a home router, or any other device that uses NAT, [configure your router]("https://help.ubuntu.com/community/ServersBehindNAT#Procedure") to send connection attempts on port 22 (but not port 5900) to your PC 
So my questions are:

1. I installed a fresh version of Ubuntu 11.4, should I be concerned about step 2? If so, how can I allow incoming connections on port 22 from anywhere, and on port 5900 from localhost?

2. Regarding step 3, I'm using NETGEAR model DGN1000 router. Is that something that I should do from the router's setting page or it's some commands that I should pass through SSH?

Please clarify, your help would be greatly appreciated.

---

### Post by dcstar on 2011-07-19
> **emurad said:**
> 
.........
2. Regarding step 3, I'm using NETGEAR model DGN1000 router. **Is that something that I should do from the router's setting page** or it's some commands that I should pass through SSH?


Yes, it has nothing to do with Ubuntu, it is your networking equipment.

---

