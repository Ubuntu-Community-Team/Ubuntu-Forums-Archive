---
title: "Game IP Address"
date: 2010-06-30
forum: General Help
---

### Post by crazyamerican on 2010-06-30
I play Warzone2100 frequently and I noticed that in the multiplayer menu, it gives me the option to connect to a game via the Lobby or IP address. I was wondering how to find the IP address needed for someone to connect to my computer and play. Clarify: I need to know where to find the IP address that my friend has to enter in this menu in order to connect to my machine.

Thanks,
crazyamerican

---

### Post by mwolfe on 2010-06-30
This would be your WAN address, or the one that is seen to your outside network.
To get this address type the search "my ip" in google and click the first link.
This is assuming you arent connected directly to the internet but that you are behind a router which is setup with NAT (network address translation), which basically means you have your own internal network.
If you do have a router, and thus you would be using NAT, you need to setup port forwarding so that when your buddy tries to connect to you the router will forward you this traffic. This means you need to find out what port the game uses to serve the game. It may be configurable. Since its a game its most likely UDP you need to forward but you may need tcp as well. I'm not really a gamer so I can't help you too much there, but I do know that typically games use UDP since they require low latency connections instead of reliable delivery (which tcp offers)

---

