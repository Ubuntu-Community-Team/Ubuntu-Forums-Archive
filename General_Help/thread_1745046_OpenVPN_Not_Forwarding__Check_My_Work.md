---
title: "OpenVPN Not Forwarding / Check My Work"
date: 2011-04-30
forum: General Help
---

### Post by farcefiasco on 2011-04-30
I've got my server and client to connect, but the server is not forwarding traffic through to the Internet. I've done lots of Google work and (I think) have implemented every "fix" that seems common for this problem. 

1. I've added ```
push "redirect-gateway def1"
``` to my server.conf file. 

2. I've edited /etc/sysctl.conf to include ```
net.ipv4.ip_forward=1
```3. I inputed ```
echo 1 > /proc/sys/net/ipv4/ip_forward 
```4. I configred iptables thusly:

> iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -A FORWARD -s 10.8.0.0/24 -j ACCEPT 
iptables -A FORWARD -j REJECT iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
and then added it to /etc/rc.local and made the script executable to run on startup


5. I installed dnsmasque and added ```
push "dhcp-option DNS 10.8.0.1"
``` to server.conf

I then started the server and clients with sudo openvpn server.conf / client.conf

**This is the output from client.conf**

[http://pastebin.com/VESaLCG8](http://pastebin.com/VESaLCG8)

**And the output from server.conf**

[http://pastebin.com/nS2RzcTD](http://pastebin.com/nS2RzcTD)


**My client.conf file**

[http://pastebin.com/zHuEW9R6](http://pastebin.com/zHuEW9R6)
[B]
And my server.conf file[/B]

[http://pastebin.com/cb236WuL](http://pastebin.com/cb236WuL)

I tried uncommented the DNS push and inputing the IP directly to avoid lookup, but nothing.  I also deleted all but the last entry in the iptables, as that seems to be the most common entry. 

If some knowledgeable folk could look all this over for me and give me an idea what the hell I'm doing wrong, I'd greatly appreciate it.

---

