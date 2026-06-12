---
title: "DSL Connection"
date: 2011-02-26
forum: General Help
---

### Post by shashanksingh on 2011-02-26
Hello. I am having a network problem here.

When I add a dsl connection through my nm-applet, I fill in the username, service name and password, and it fails to connect.
The connection works fine with the same credentials in windows7.
My ISP has two different servers that is distinguishes using the service name. I am told windows recognises the service name and goes in the appropriate server where my account is present, whereas ubuntu (nm-applet) does not.

However, when I tried pppoeconf, it works but only for sometime.
My ISP tells me there is no other solution but to purchase a router.
Pls help:confused:

---

### Post by anirudhtomer on 2011-02-26
> My ISP tells me there is no other solution but to purchase a router.
Where comes this router in this between. It has got nothing to do with your problem. Its job is to forward the packets that you ask it to. So do not change your router, that won't help.

My ISP is BSNL and their service name is "dataone". Even if I do not provide it the service name or change it to "xyzblablabla" it works fine. (BSNL provides only a single service to its customers by the way!!! :) )

I connected using Network Manager and then I did ```
ifconfig
```
```
ppp0      Link encap:Point-to-Point Protocol  
          inet addr:117.195.102.6  P-t-P:117.195.96.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:1421 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:355226 (355.2 KB)  TX bytes:169679 (169.6 KB)

```

So if you connect via pppoeconf or network manager, internally a point to point connection is formed finally. 

[B][I]So if connecting using one works and with the other one don't(when internally they do the same thing) then there is a problem with the other one. ie. Your Network Manager. Try using some other Network Manager.
[/I][/B]

Just out of curiosity!!!, I wanna know what are the two service names provided to you by your ISP.
Usually when various service name provided to the customer they are for different service not for the same one, like on mobiles "AIRCEL GPRS", "AIRCEL MMS", "AIRCEL Pocket Internet". etc are for different purpose. 

Similarly I think if your ISP has provided you with two service names then they must be for two different services, not for providing the same. (Internet surfing in your case).

---

### Post by shashanksingh on 2011-02-27
Here's the issue in detail. First, the service name of my isp was
'instanet'.

Even if I didnt provide the service name, it used to work fine.
Then, another company brought instanet, so now they have a new server. The "service" of the new server is 'dnainfotel' and trhe previous is 'instanet'. They are transfering all accounts from instanet to dnainfotel.

So, when in Windows, I give the service name 'dnainfotel', it connects to the appropriate server.

But in ubuntu, mostly the requests go to the previous server and it doesnt connect. After a few days, I have seen it connects from both nm-applet and pppoeconf allbeit once in five-six attempts or mostly does not connect.

What I am thinking is, why does it work absolutely fine in windows but not in ubuntu???

---

### Post by sidramalik100 on 2011-04-18
Connect to your service provider company me currently using the Wateen connection and it is working very well in my Area and i think Wateen is the best in all you have also need to install the window again and also connect to your service provider Company may be they can provide you better tips then us

---

