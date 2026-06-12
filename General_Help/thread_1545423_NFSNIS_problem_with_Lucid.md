---
title: "NFS/NIS problem with Lucid"
date: 2010-08-03
forum: General Help
---

### Post by Abhinav Gupta on 2010-08-03
Hi,
 I recently set up a network with Ubuntu 10.04 Desktop installed on three computers, with NFS/NIS installed on one of them, to make it act as a server (the server machine also had Ubuntu Desktop installed on it, not Ubuntu server), and the other two machines as clients. The server machine was also set to IP forward, so that the client machines could access internet through it. This was set up with a fresh install of 10.04, **without running any updates**. The network was running fine, till I ran updates on the server. The updates removed the NFS/NIS configuration, and also the IP forwarding (the /proc/sys/net/ipv4/ip_forward entry was reset to 0). The clients cannot access the server, and when the server is rebooted, it gives a server error before the login screen comes up. 
  This is really frustrating, and even if I reconfigure NFS/NIS and IP forwarding again, will the next update mess it up????
Is there a way out?
Thanks!

---

