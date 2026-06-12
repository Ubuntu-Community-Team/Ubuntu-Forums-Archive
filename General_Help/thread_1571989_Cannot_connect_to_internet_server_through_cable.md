---
title: "Cannot connect to internet server through cable"
date: 2010-09-10
forum: General Help
---

### Post by erebus314 on 2010-09-10
Hi, I have recently downloaded and installed ubuntu 10.4, and I am finding it impossible to connect to the internet.

I connect to the internet through an Ethernet cable. My university (Tuebingen, Germany) provides the internet through this server:

[http://10.196.128.11/upload/custom/green/welcome.html](http://10.196.128.11/upload/custom/green/welcome.html) (English link).

When I open my browser in windows vista (I have a duel-boot system), my browser (Firefox) automatically goes to this page, and I log in, and am able to then use the internet.

Ubuntu also searches for this 10.196.128.11 server, but it continually states "waiting for server to respond". I have checked all the settings I could find in windows and compared them to the ones in ubuntu, and they seem to be identical to me. I am using firefox in ubuntu too so I cannot understand the problem.

I would be grateful if anyone has any idea or advice about this problem. Please tell me if what I have written is unclear or if I can provide any more details.

---

### Post by lovinglinux on 2010-09-10
Have you tried to disable ipv6? See the fifth item on [this list]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html").

---

### Post by erebus314 on 2010-09-10
Thanks for the reply. IPv6 does seem to be disabled. Also it is not that the website keeps loading, it isn't loading at all. It just says: "waiting for 10.198.128.11 to respond". And I can't connect to the site by directly typing into the URL bar either its IP address or the full URL of the page windows loads.

---

### Post by Gunman1982 on 2010-09-10
The link won't work for anyone outside the campus/accomodation since it points to a internal ip.
 
You should check your proxy settings on the windows firefox.

Don't have any other ideas right now. Did you search the website of your university for information about connecting with ubuntu or linux overall?

Oh yeah and you could try if you can even reach the server by 'ping 10.198.128.11', and for a more expert try 'telnet 10.198.128.11 80' which tries to connect to the http port of the server. If you et a prompt you at least know its accepting a connection.

Some more information could help too:
output of 'sudo ifconfig'
output of 'sudo route -n'

---

### Post by erebus314 on 2010-09-10
Ah, sorry I didn't realise that. Could you please explain what you mean by my firefox proxy settings? I think I have checked them and found them to be identical to the ubuntu ones, but perhaps I have not, or done it wrong. The setting say it is set to use the system settings, and the windows settings, when I click details on the status page, are the same as the ubuntu ones.

The only advice I can find on the university website for linux is when connecting using the wireless network on the campus. I will go to the IT department next week, but since the problem is when I connect the cable in my student flat I am not sure if they'll be able to replicate it.

---

### Post by erebus314 on 2010-09-10
Ping works, but telnet cannot connect. This is the output from those commands:

erebus@erebus-314:~$ telnet 10.196.128.11
Trying 10.196.128.11...
telnet: Unable to connect to remote host: Connection timed out
erebus@erebus-314:~$ sudo ifconfig
[sudo] password for erebus: 
eth0      Link encap:Ethernet  HWaddr 00:23:54:0f:ff:d1  
          inet addr:10.196.155.211  Bcast:10.196.255.255  Mask:255.255.128.0
          inet6 addr: fe80::223:54ff:fe0f:ffd1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17056 errors:64 dropped:0 overruns:0 frame:64
          TX packets:206 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1338012 (1.3 MB)  TX bytes:24609 (24.6 KB)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:1f:3f:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

erebus@erebus-314:~$ sudo route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.196.128.0    0.0.0.0         255.255.128.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.196.128.1    0.0.0.0         UG    0      0        0 eth0
erebus@erebus-314:~$

---

### Post by Gunman1982 on 2010-09-10
> **erebus314 said:**
> Ping works, but telnet cannot connect. This is the output from those commands:

erebus@erebus-314:~$ telnet 10.196.128.11

You have to use the port too when you use telnet. Example:
```
xxx@xxx:~$ telnet 209.85.135.104 80
Trying 209.85.135.104...
Connected to 209.85.135.104.
Escape character is '^]'.
^] 

telnet> close
Connection closed.
xxx@xxx:~$ 
```
In your case telnet 10.196.128.11 **80**

---

### Post by erebus314 on 2010-09-10
Ok, I did it again, this time with the port, and it connected - but only for a few seconds. Then it said the connection was terminated by a foreign host

---

### Post by Gunman1982 on 2010-09-10
> **erebus314 said:**
> Ok, I did it again, this time with the port, and it connected - but only for a few seconds. Then it said the connection was terminated by a foreign host

Mhh so the server allows connections, that it closes the connection you establish with telnet is not so surprising. 

Seems that everything looks ok from your side. Don't really know what else you can do. Maybe try another browser (epiphany, opera, that gogle thingy).

---

### Post by erebus314 on 2010-09-12
I tried connecting with a different browser and got the same result. As far as I can see the only difference is that I'm logging in from a ubuntu machine. Is there any way to fool this server so that it thinks I'm using a windows machine?

---

