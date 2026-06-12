---
title: "opera,firefox,google chrome no net but skype works"
date: 2010-02-18
forum: General Help
---

### Post by graham70 on 2010-02-18
Good day all 
Just recently I have bought two wireless broadband modems (Australia telsta next G). Have to give the ubuntu teams a thumbs up for support for these devices as they work strait out of the box. Now for my problem is my web browsers work sometimes when login on the broadband service. I also did a fresh in stall of Google chrome . The funny thing is that skype works fine so I have a Internet connection. My work around at them moment is keep to restart the computer and trying a web browser on about the fifth or less/more I get a web browser that works ( one works all work). 
looking around the web for help found that in Firefox IPv6 gives this problem. to fix in firefox I opened "open:config" and changed "network.dns.disableIPv6" to "false" . This didn't work 
 
one laptop running ubuntu 9.04 32bit the other is running ubuntu 9.10 64bit 

any help will be great

---

### Post by NT4usB on 2010-02-19
Sounds like a domain name server (dns) problem.
Skype connects to an ip address. 
Your browser(s) are trying to resolve a domain name into an ip address before they can connect.

---

### Post by akakingess on 2010-02-19
> **NT4usB said:**
> Sounds like a domain name server (dns) problem.
Skype connects to an ip address. 
Your browser(s) are trying to resolve a domain name into an ip address before they can connect.

I tend to agree, but what doesn't make sense is why they work sometimes and not others, I would definitely disable IPv6 at this point, and try DNS 4.2.2.2 and 4.2.2.3, as those have never gone down for me, and my ISPs has been shaky at times. Just something to try at this point, but I can't think of what would cause DNS to work one minute and not the next. Unless the servers are just that bad, but then nobody would use that ISP (IMHO).

---

### Post by graham70 on 2010-02-19
thanks both of you for your replies.
first question how can I disable ipv6 system wide 
second question how do I change my DNS to 4.2.2.2
the isp I am using is in Australia telstra big pond. primary DNS 139.130.4.4 Secondary DNS 203.50.2.71
thanks again

---

### Post by JackRock on 2010-02-19
To disable IPv6, you do it per network connection.  So go to System > Preferences > Network Connections.

Choose the network connection you have (perhaps Eth0) - whichever has a full IPv6 address.  Click "Edit".
Go to the IPv6 tab in the new window, and choose "Ignore" in the Method drop-down box.

---

### Post by Julita on 2010-02-19
You can also disable ipv6 by adding the following line to /etc/modprobe.d/blacklist:
blacklist ipv6

---

### Post by akakingess on 2010-02-19
Thank you JackRock and Julita, as I had already signed off for the night, I hate to suggest stuff and leave but I was dead tired, and graham70, if you have any more questions, but don't want to continue the thread you can IM me.  Good Luck.

---

### Post by NT4usB on 2010-02-19
> **graham70 said:**
> thanks both of you for your replies.
first question how can I disable ipv6 system wide 
second question how do I change my DNS to 4.2.2.2
the isp I am using is in Australia telstra big pond. primary DNS 139.130.4.4 Secondary DNS 203.50.2.71
thanks again

You'll find the dns settings in your network manager. The default is server assigned but you can set them manually. Sometimes your router won't let the server through to assign them.
Might also check your router settings. I've had routers that handled the dns internally so I would set the dns in network manager to the router ip address.

btw, I pinged the two dns addresses you list and the first one doesn't answer. Might try pinging them next time you can't connect, see if they're up.```
ct@g41p2:~$ ping 139.130.4.4
PING 139.130.4.4 (139.130.4.4) 56(84) bytes of data.
^C
--- 139.130.4.4 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7016ms

ct@g41p2:~$ ping 203.50.2.71
PING 203.50.2.71 (203.50.2.71) 56(84) bytes of data.
64 bytes from 203.50.2.71: icmp_seq=1 ttl=114 time=265 ms
64 bytes from 203.50.2.71: icmp_seq=2 ttl=114 time=282 ms
64 bytes from 203.50.2.71: icmp_seq=3 ttl=114 time=258 ms
64 bytes from 203.50.2.71: icmp_seq=4 ttl=114 time=255 ms
64 bytes from 203.50.2.71: icmp_seq=5 ttl=114 time=291 ms
64 bytes from 203.50.2.71: icmp_seq=6 ttl=114 time=228 ms
^C
--- 203.50.2.71 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5002ms
rtt min/avg/max/mdev = 228.733/263.758/291.994/20.267 ms
ct@g41p2:~$ 

```

---

