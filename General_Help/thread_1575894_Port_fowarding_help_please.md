---
title: "Port fowarding help please"
date: 2010-09-16
forum: General Help
---

### Post by unbuntunewb on 2010-09-16
so I am trying to create an ssh socks proxy and I have openSSH on my machines and configured my router as explained here

[http://www.youtube.com/watch?v=GWPUdW1kIJA](http://www.youtube.com/watch?v=GWPUdW1kIJA)

however I still cannot get a connection, I believe I also need to set up my modem to accept the connection. According to portfoward.com any IP that is not

a) 10.0.*.* to 10.255.*.*
 
b) 172.16.*.* to 172.31.*.*
 
c) 192.168.*.* 

Or any of the other reserved IP ( All of them are at [http://en.wikipedia.org/wiki/Classful_network](http://en.wikipedia.org/wiki/Classful_network) under the heading of **Some addresses are reserved for special uses** ), is a public IP.

#2 You can't use any public IP without contacting your ISP. 

#3 And if you have a static public IP address, you would have to use the settings that they gave to you. [IMG]http://forum.portforward.com/yabbfiles/Templates/Forum/default/wink.gif[/IMG]

my question is how do I set up modem for port fowarding (if indeed that is the problem) and what IP range can I use without having to contact my ISP?

---

### Post by 98cwitr on 2010-09-16
modem's dont do port forwarding...you need a router to setup port forwarding. What port have you assigned for SSH? DONT USE THE DEFAULT PORT 22!

Read this [https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)

---

