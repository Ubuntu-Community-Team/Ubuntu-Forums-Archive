---
title: "Ports used by KTorrent"
date: 2012-10-03
forum: General Help
---

### Post by thunder686 on 2012-10-03
It appears that ktorrent is using additional ports than the ones listed in the setting. In the setting I see it using port 6881 for bitorrent, port 8881 for udp tracker and port 7881 for DHT. My firewall is set to block all incoming and outgoing connections except for the ports that I specified. I tried opening all the three ports but it still unable to connect to the trackers or download but when I set the firewall outgoing setting to allow, I get ktorrent connecting to the trackers and downloading.

---

### Post by rai4shu2 on 2012-10-03
I'm guessing you have the UFW rules in a bad order. Always put your specific rules before the more general ones. See:

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by thunder686 on 2012-10-04
Here are my firewall rules. As it can be seen, my specific rules are set to allow so I guess order does not matter here.

---

### Post by rai4shu2 on 2012-10-04
You have outgoing set to default deny? What's up with that? Which Firewall is that, anyway?

---

### Post by thunder686 on 2012-10-04
Thats GUFW a  GUI front for UFW.

---

### Post by rai4shu2 on 2012-10-04
Unless you don't trust the applications you're running, then there's no reason to block outgoing ports. Obviously, the more outgoing connections you can make, the faster your download can go.

---

### Post by thunder686 on 2012-10-21
I installed [leopard flower]("http://sourceforge.net/projects/leopardflower/") which is an application level firewall on my kubuntu 12.04. Now I can control what can use the internet. BTW it is alot easier and user friendly than apparmor.

---

