---
title: "Question Port forwarding in Bittorrent client in internal network with nat I have an"
date: 2010-04-09
forum: General Help
---

### Post by lgp171188 on 2010-04-09
I have an internal network behind a server <10.0.0.1> connected to the internet that NATs my ip <10.17.11.88> only. The packets from my internal machine are forwarded to the internet after SNAT to the public ip of the server. NAT is not allowed to any other ip addresses. When I use Transmission Bittorrent client to download torrents, I saw this in the message log and I couldn't understand it

```

Sat Apr 10 02:28:39 2010	     	Port Forwarding (UPnP)	Found Internet Gateway Device "http://10.20.0.244:2869/"
Sat Apr 10 02:28:39 2010	     	Port Forwarding (UPnP)	Local Address is "10.17.11.88"
Sat Apr 10 02:28:44 2010	     	Port Forwarding (UPnP)	Port forwarding through "http://10.20.0.244:2869/", service "".  (local address: 10.17.11.88:51413)
Sat Apr 10 02:28:44 2010	     	Port Forwarding (UPnP)	Port forwarding successful!
Sat Apr 10 02:28:44 2010	     	Port Forwarding	State changed from "Not forwarded" to "Forwarded"

```

The thing is that this 10.20.0.244 is not my machine and doesn't have access to the internet at all. What is happening here? Can anyone help me?

---

