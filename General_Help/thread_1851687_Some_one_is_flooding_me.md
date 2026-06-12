---
title: "Some one is flooding me"
date: 2011-09-28
forum: General Help
---

### Post by eyalmmm on 2011-09-28
Hello 
ive bought a box for games server hosting in israel 
some one is flooding me i see i have 9310.80 in recive in ibmonitor
i have only 10 megas internet 
so heres my questions:
1)how do i know who is flooding me
2)how can i see the methode he is flooding me 
3)how can i know what port is he flooding( and how to block it )
4)how can i block any connection from this ip 
5)is that posible to notify who is flooding me and block him by itself
I need your help very much becouse im getting very mad couse of this 
(my box ip : 213.8.155.48 ) 
if u can help me with this information please help me im very new with centos and also linux

---

### Post by Old_Grey_Wolf on 2011-09-28
You set up a game server. Apparently it is for Counter Strike. Your server is listed at [http://www.game-monitor.com/cstrike_GameServer/213.8.155.48:40054/Counter_Strike_-_ServForU.net.html](http://www.game-monitor.com/cstrike_GameServer/213.8.155.48:40054/Counter_Strike_-_ServForU.net.html) and possibly other places.

Edit: Another listing [http://en.stats4game.com/search?q=213.8.155.48](http://en.stats4game.com/search?q=213.8.155.48)

If you do something that gets your game server advertised; then, be prepared for the Internet traffic. I doubt it is a DoS attack. If you have a router, you could check the router's logs to determine where the traffic is coming from. If you don't have a router, you could look into Wireshark (it's in the repositories) to identify the source of the traffic. However, I think you are just getting the Internet traffic because you advertised your game server in some way.

By posting your IP address, you invited a few of us to ping your computer as well. 

Edit: And, it wasn't responding to pings.

:)

---

