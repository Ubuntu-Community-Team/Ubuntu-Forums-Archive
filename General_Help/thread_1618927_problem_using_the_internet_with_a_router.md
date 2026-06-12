---
title: "problem using the internet with a router"
date: 2010-11-11
forum: General Help
---

### Post by Acradon on 2010-11-11
Hi, 

I have been accessing the internet via a direct connection to my PC. However, I just bought a router (DLink WBR-1310) to also be able to access the internet wireless with my laptop. I had a few problems setting it up, but finally got it working. The next morning I was happy to listen to online radio on the laptop while having breakfast. After coming home from work the network did not connect anymore. I have reconfigured the router time and time again. Everything seems to be in order, but whenever I try to access the internet with firefos it says that the server is not available or that I might have problems with my firewall or proxy settings. I never really understood those proxy things. Is there something I am missing? 

Do I have to install something on ubuntu?

---

### Post by c2tarun on 2010-11-11
> **Acradon said:**
> Hi, 

I have been accessing the internet via a direct connection to my PC. However, I just bought a router (DLink WBR-1310) to also be able to access the internet wireless with my laptop. I had a few problems setting it up, but finally got it working. The next morning I was happy to listen to online radio on the laptop while having breakfast. After coming home from work the network did not connect anymore. I have reconfigured the router time and time again. Everything seems to be in order, but whenever I try to access the internet with firefos it says that the server is not available or that I might have problems with my firewall or proxy settings. I never really understood those proxy things. Is there something I am missing? 

Do I have to install something on ubuntu?


there is a small button on the side of delink router. press it and try restart your system. also right click on the network icon on upper right corner and check whether wireless connection is enabled or not...
please reply your progress

---

### Post by Bucky Ball on 2010-11-11
> **Acradon said:**
> Do I have to install something on ubuntu?

No. You need to find the root of your problem. Wireless card working okay?

* Open a terminal (Applications->Accessories->Terminal) and copy/paste this:

```
iwconfig
```Then this:

```
ifconfig
```Copy/paste the output here unless you manage to fix the prob from there. You need to make sure the router is set up as a DHCP server so it can serve you an IP address (if that is what you're after - setting up static IP is another matter). 

If you are using static IPs on your home network (LAN) this is a different setup on the router (you don't want it serving IPs).

Best bet? Plug a cable directly between the router and the computer, don't even worry about internet for the moment, and make sure that the router's set up correctly for:

* Your ISP and with the DNS servers, etc, that they have assigned (this usually involves finding out the IP addresses for their servers for wireless - not so for wired as you are generally served them)

... And your computer is set up with:

* The correct ESSID and WEP/WAP key, or whatever else security you need, and these details match your router.

If you have not NAMED your router (in this case an AP or Access Point) and given it some sort of security key (WEP or any other kind), do so now and make sure your computer matches that by heading to (and this depends on the release and software you're using) either:

System->admin->Network

... and unlocking, or right click on the network icon and 'Edit Connections'.

Summing up:

- Router must have ESSID ('mynetwork' or what your like) and security key.
- Your wireless boxes'  'Network' settings (ESSID and security key), wherever they are set, must match with the router's.

I really hope this give you a hand getting closer to solving your issue. :)

UPDATE: c2tarun may have fixed your prob much more simply. !

---

### Post by coldraven on 2010-11-11
Also make sure that your routers firewall is enabled and  that you have  a secure password to access it.
I don't know what default password is set for your router but I would change it anyway to something fiendishly complicated . Remember that this password is protecting your system from the rest of the world :)
Let your browser remember the password and if you do lose it you can always do a hardware reset on the router. That would mean having to re-configure it though.

---

### Post by mcduck on 2010-11-11
> **coldraven said:**
> Also make sure that your routers firewall is enabled and  that you have  a secure password to access it.
I don't know what default password is set for your router but I would change it anyway to something fiendishly complicated . Remember that this password is protecting your system from the rest of the world :)
Let your browser remember the password and if you do lose it you can always do a hardware reset on the router. That would mean having to re-configure it though.

Actually a firewall isn't necessary in most cases (at least if you don't have Windows computers in the network) and the NAT provided by the router will already go a long way. 

Also, any sensible router will not allow accessing router settings from WAN side. The ones that do usually require you to specifically enable that feature first.

So in the end the things you should actually worry about are all related to wireless networks. Use decent wireless security (WAP2) and good password for that. Apart from configuring the wireless network, it's usually enough to just set both the router and all machines on the network to use DHCP.

---

### Post by Acradon on 2010-11-11
How do I find out what my ISP is (I mean DHCP, static or whatnot) I never got any IP adress or something like that. I use a wireless ISP (living in the country ya know). I have a cable directly into my PC with a small powersupply hooked in between, which works fine, but when I hook the router in between I can't access the web at all. It doesn't even time out or take a while, it goes straight to server not found. 
I don't think that the wireless settings are the issue, as I have the same problem with my desktop which is LAN connected to the router. 

I get some info on my connection right now (direct plug-in) that states IP adress, broadcasting adress, Subnet mask, Default route and primary as well as secondary DNS adresses. These are somewhat different fro when I use the router. COuld this be the problem? If so, where do I need to put in the information when setting up the router?

---

### Post by Acradon on 2010-11-11
hmmm, I think I figured it out....not happy though. It seems that my rouer has a problem. I saw the Internet light blink when I plugged the Internet cable in, then it went dead. I was trying to load a page and nothing happened. So I unplugged the cable and plugged it back in. now it works....wonder whether there is a loose connection or something inside.
Ah well it was second hand and only cost 20 bucks....what can you expect.

---

