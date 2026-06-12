---
title: "What is the advantage and disadvantage of VPN over TOR"
date: 2009-12-24
forum: General Help
---

### Post by emigrant on 2009-12-24
and how to configure a VPN in jaunty? :confused:
thank you very much.

---

### Post by 3rdalbum on 2009-12-24
A VPN and Tor are two completely different things.

Tor is an anonymiser - it attempts to prevent the destination computer from knowing the real source of the connection it recieves. It does this by pushing your data around a cloud of other Tor nodes for a while until it reaches an "exit node", at which point it is sent to the destination. The destination believes that the connection originated at the exit node. Tor can be evesdropped by any other Tor user whose computer recieves your data, but the evesdropper probably won't know which computer the data came from.

A VPN is an encrypted direct connection from your computer to another computer. The other computer is typically inside a corporate network and your is outside. It allows you to log into your corporate network from anywhere you are, without being evesdropped. The destination computer knows the location of your computer.

Two completely different things with different purposes.

What do you want Tor or a VPN for?

---

### Post by emigrant on 2009-12-24
hi, thank you very much for your reply.
from what i knew before, TOR anonymises the sender and VPN encrypts the message, i wanted to combine both. so sender is anonymous as well as the message is encrypted.

from your reply, if i have correctly understood, VPN is established only between two already known nodes?
i mean, can i browse this forum or any arbitrary site through VPN?

thank you very much.

---

### Post by LoneWolfJack on 2009-12-24
think of a VPN connection as a second gateway layer. your first gateway is the server of your ISP you connect to. with VPN, you configure your connection in a way so that your ISP's gateway is only "talking" to the VPN server (2md gateway) over an encrypted connection and the VPN server will  talk to all the servers you initiate a connection with.

that way, your ISP will only know you exchange packets with your VPN server. the rest of the world will only see your VPN server's IP.

if you can trust the VPN server (i.e. if you know/trust the company running it doesn't store any connection data), it should be as secure as TOR.

the main advatnage VPN has over TOR, however, is that you have a much lower latency (AFAIK, at least) and a much greater bandwidth because you can rely on the network connection of your VPN server.

---

### Post by emigrant on 2009-12-24
thank you very much for your reply LoneWolfJack,
so that means, my ISP doesknow which sites i browse? and it is not better than TOR interms of security.
and how to assess the trustworthyness of a VPN server? (i think this question is because i don't know how to configure a VPN connection) :confused:

thank you very much.

---

### Post by timgood on 2009-12-24
I think you are still missing the point. VPN is used to attach to networks like corporate/university/college and is not used for general web-browsing. To attach to a VPN you need to know each networks specific settings and you need each network to allow you access. If all you want to do is browse the internet anonymously, you can use TOR or anyone of the plugins for Firefox etc. that allow you to do this.

---

### Post by 3rdalbum on 2009-12-24
A VPN basically extends an existing network so that you can connect to it remotely. All traffic is encrypted. It is more "secure" than Tor. Tor is not secure. Tor traffic is not encrypted, it is merely anonymous.

VPN - The letters stand for "Virtual Private Network" - it makes your computer think it's connected directly to a private network, when in fact it's only virtually connected by using the Internet.

You have to trust the VPN server. It decrypts your data and can potentially read it all. That's the point.

---

### Post by emigrant on 2009-12-24
thank you very much timgood

---

### Post by ladi on 2011-07-03
> **3rdalbum said:**
> A VPN basically extends an existing network so that you can connect to it remotely. All traffic is encrypted. It is more "secure" than Tor. Tor is not secure. Tor traffic is not encrypted, it is merely anonymous.

VPN - The letters stand for "Virtual Private Network" - it makes your computer think it's connected directly to a private network, when in fact it's only virtually connected by using the Internet.

You have to trust the VPN server. It decrypts your data and can potentially read it all. That's the point.


so what is the best way to stay anonymous? i'm using Tor right now and it seems my data is being compromises between my ISP and destination. else, maybe at Tor nodes in the network.

urgent reply would be appreciated.

---

### Post by ladi on 2011-07-03
> **emigrant said:**
> and how to configure a VPN in jaunty? :confused:
thank you very much.
pls check below.... a new question?

---

