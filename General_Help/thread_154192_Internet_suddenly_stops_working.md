---
title: "Internet suddenly stops working?"
date: 2006-04-02
forum: General Help
---

### Post by arock99 on 2006-04-02
Internet suddenly stops working?

Hello,
Not sure if I somehow got hacked or what but as of yesterday my network on my linux machine does not work anymore...
I am behind a software firewall (shorewall) as well as my router's build-in hardware firewall.

Here is my network setup:

Internet goes through Router #1.  My linux machine is behind router #1.  Router's internal address is 192.168.1.1
behind router #1 I also have two other devices one of which is another router (we will call that Router #2).  Behind router #2 i have my laptop...internet works 100% with my laptop (Windows box).
Back to my Linux box....I can SSH to this box locally as long as I try connecting to its internal IP address although now the connection seems to take longer to connect than it used to (before it was pretty instantaneous but it now takes 3-4 seconds to connect).
The linux box cannot connect to the internet but can connect to my Tomcat instance on my Windows box.  Here's the weird part....I can connect to Router #1 from my Windows box at 192.168.1.1 but can no longer connect to even my router from my Linux box.

As I mentioned everything worked fine just a couple of days ago

---

### Post by mlalkaka on 2006-04-02
```

                +-----------+
                | Router #1 |
                +-----------+
               /             \
+----------------+            \
| Linux Computer |             +-----------+
+----------------+             | Router #2 |
                               +-----------+
                                            \
                                             +------------------+
                                             | Windows Computer |
                                             +------------------+

```

Does the above ASCII art image represent your network topology?
I don't know very much about networks, so I'll try to give some tips that have helped me in resolving network issues.
First, I think you should try rebooting/restarting both routers.
If that doesn't work, maybe the configuration on router #1 is blocking Linux Computer from internet access? 
Another thing to check is whether Linux Computer is able to resolve hostnames. Try the command "host www.google.com"; if it cannot get the IP addresses of [www.google.com](www.google.com), then maybe the DNS servers are the problem. In this case, try accessing a site using its IP address rather than its domain name (you can find the IP address of a website using the ping command on Windows Computer).

I have had network problems before, but the cause of the problems have never been GNU/Linux. So I don't think the problem is Linux this time either (especially since everything was working fine a couple of days ago). However, some people have said that disabling IP version 6 (kernel module ipv6) support in the kernel has fixed problems because not all routers support IPv6 yet.

Hope this helps, 
Malcolm

---

### Post by cmatheson on 2006-04-02
could you post the output of the following commands?

ifconfig -a
cat /etc/resolv.conf
ip route show

---

### Post by arock99 on 2006-04-02
Rebooting Router #1 worked...
Something so simple and yet I didn't think of it :)
Thanks for the help guys...

by the way your diagram is correct

---

### Post by jamesr on 2006-04-02
Can you ping the routers, also am I to assume that you have disabled the DHCP server on router 2

---

