---
title: "wireless settings making me crazy :("
date: 2010-03-07
forum: General Help
---

### Post by ibrahim.k on 2010-03-07
Hi,

this is really a hard issue somehow because I am not skilled with networking.
i will try my best to explain


at the office we have a wireless router for the internet.
and we have a server with windows server installed on it.
I have connected the server to the wireless router via an ethernet cat6 cable
now i want from the wireless router to give me both at the same time
1-internet connection
2-ability to connect to the server via terminal desktop connection

the problem is that when i use (dhcp) i can get internet connection only
and when i use manual ip configuration i lose the internet connection but i can connect the server
please help me regarding this issue this is very important

thnx in advance
internet

---

### Post by zaphod777 on 2010-03-07
Sounds like you have  DHCP turned on both your server and the router. 

Make sure that the DHCP on your server is set to include the correct default gateway of the router and has the dns information pointing to the router.

If you are running active directory and DNS on your server make sure that the DNS in DHCP are listed as the server being the primary DNS and the router being the second DNS. 

Doing an ifconfig (ubuntu) or an ipconfig (windows) on the client when they can connect to the server but no internet should tell you everything.

Probably no or incorrect DNS and/ or default gateway.

Also make sure that the servers static ip address settings are set correctly for your subnet.

---

### Post by ibrahim.k on 2010-03-07
Thnx for the fast reply zaphod777 the problem is that I can't change the router or server settings,
and i dont know much about networking
so on wireless when i want to get internet connection i change the settings to dhcp
when i want to connect to the server i change the ip settings to the following
192.168.10.1
255.255.255.0
0.0.0.0  (i cant leave it blank)

---

### Post by zaphod777 on 2010-03-07
Then you probably don't want to go mucking around with the server.

What IP settings do you have on your machine when you can connect to the server?

It isn't the best solution but it should "work" is when you can connect to the server add  8.8.8.8 and 8.8.4.4 to the DNS server settings on your computers. It is google's public dns servers.
directions on how to do it are here:
[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

If it is only for a few machines then it won't be too bad. 

If that doesn't work then please give me the output of ipconfig /all on Windows machine both when you can connect to the server and when you can connect to the internet. That should tell me what the problem is right away.

---

### Post by ibrahim.k on 2010-03-07
when i connect to the server i use this settings 
Manula
192.168.10.1
255.255.255.0
0.0.0.0  (i cant leave it blank)
dns (i keep it blank)
according to the dns i have one field only for dns
where should I place the next one ??
i am using 9.10 
the field under dns is domain search
by the way google doesnt allow my host to use this
[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

it is forbidden here by google thats what i get
after changing the proxy it worked

---

### Post by ibrahim.k on 2010-03-07
this is the output from ipconfig /all (the server windows 2003)

 
C:\Program Files\PostgreSQL\8.3\bin>ipconfig /all 
 
Windows IP Configuration 
 
   Host Name . . . . . . . . . . . . : uu 
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Broadcast 
   IP Routing Enabled. . . . . . . . : Yes 
   WINS Proxy Enabled. . . . . . . . : Yes 
 
Ethernet adapter Local Area Connection: 
 
   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Realtek RTL8168/8 
et NIC 
   Physical Address. . . . . . . . . : 00-1D-92-7C-66-F6 
   DHCP Enabled. . . . . . . . . . . : No 
   IP Address. . . . . . . . . . . . : 192.168.90.30 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0 
   IP Address. . . . . . . . . . . . : 192.168.10.30 
   Subnet Mask . . . . . . . . . . . : 255.255.255.192 
   Default Gateway . . . . . . . . . : 192.168.10.10 
   DNS Servers . . . . . . . . . . . : 192.168.2.9 
                                       192.168.2.14

according to the router i can see this settings from the connection information
broadcast adress 192.168.0.255
subnet mask 255.255.255.0
default route 192.168.0.1
primary dns 192.168.0.1

---

### Post by zaphod777 on 2010-03-07
okay on your IP settings you need to set you ip address to anything other than 192.168.10.1 that is your routers ip address. 192.168.10.50 should work fine.

the default gateway should be set to 192.168.10.1
for the DNS set it to 192.168.10.1

then it should use the routers DNS settings to get to the internet. 


You mention you are using a proxy? That can throw a whole new wrench into the mix.

---

### Post by ibrahim.k on 2010-03-07
It didn't work my friend after using this settings i can connect to the server but no internet connection
this is what i have done
manual settings for the wireless connection
ip adress  192.168.10.50
dns  255.255.255.0
gateway 192.168.10.1
dns 192.168.10.1
don't worry about the proxy i can get a direct internet connection.

and please note that I get this information when i am using dhcp

ip adress 192.168.0.82
broadcast adress 192.168.0.255
subnet mask 255.255.255.0
default route 192.168.0.1
primary dns 192.168.0.1

---

### Post by pbrane on 2010-03-07
It looks like your wireless router network is 192.168.0.0 and your server is on network 192.168.10.0. Those are two different networks. You should change your router network to match your server or change your server's static IP to match your router.

---

### Post by zaphod777 on 2010-03-07
yes that looks like it.

---

### Post by ibrahim.k on 2010-03-08
Thank you very much guys . now I understand what the problem is

---

