---
title: "One computer provide Internet access to entire network"
date: 2012-05-30
forum: General Help
---

### Post by ki4jgt on 2012-05-30
I'm using Ubuntu 12.04 with two wireless cards. I have two wireless routers (one with Internet the other not). I would like to connect to the router with the Internet and then connect to the router without it and provide Internet to everyone on the router without it. Is this possible? It'll only be temporary so I don't need any additional equiptment.

---

### Post by kanikilu on 2012-05-30
Maybe I'm not understanding the question right, but I think I've done something similar, but I just simply bridged the non-internet connected router to the main one. If your routers supports bridging or repeating, I think this would be the easiest solution.

[http://en.wikipedia.org/wiki/Wireless_bridge](http://en.wikipedia.org/wiki/Wireless_bridge)

Since it sounds like everyone is within range, maybe another option is to take the non-internet connected router out of the equation and just create an ad-hoc wireless network using your 2nd wireless adapters?

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

[http://radu.cotescu.com/ubuntu-internet-connection-sharing-wireless/](http://radu.cotescu.com/ubuntu-internet-connection-sharing-wireless/)

---

### Post by ki4jgt on 2012-05-30
> **kanikilu said:**
> Maybe I'm not understanding the question right, but I think I've done something similar, but I just simply bridged the non-internet connected router to the main one. If your routers supports bridging or repeating, I think this would be the easiest solution.

[http://en.wikipedia.org/wiki/Wireless_bridge](http://en.wikipedia.org/wiki/Wireless_bridge)

Since it sounds like everyone is within range, maybe another option is to take the non-internet connected router out of the equation and just create an ad-hoc wireless network using your 2nd wireless adapters?

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

[http://radu.cotescu.com/ubuntu-internet-connection-sharing-wireless/](http://radu.cotescu.com/ubuntu-internet-connection-sharing-wireless/)

Well, I'm in range of a public wifi spot. I've tried adhocing but my iphone doesn't support it :(. My Iphone isn't in range though so I'm wanting to repeat the signal into my room by recieving it with one wireless card and sending it to the second router with the other. In any means, it's only a temporary setup so I don't want to purchase any additional hardware. The routers don't support bridging.

---

### Post by Cheesemill on 2012-05-30
It may be a bit beyond your needs but you can achieve this by setting your machine up as a NAT router:

[http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/](http://codeghar.wordpress.com/2012/05/02/ubuntu-12-04-ipv4-nat-gateway-and-dhcp-server/)

Obviously you need to change the setup above from using eth0 and eth1 to using your 2 wireless cards.
You could also forgo the DHCP server and use your second router to do this.

---

