---
title: "Use old laptop as wireless bridge"
date: 2010-06-11
forum: General Help
---

### Post by tcrowter on 2010-06-11
(If this is in the wrong place, please could a mod move it? I thought that as it crosses varies forum topics that this was the best place, but I could be wrong.)

I have an old laptop, which doesn't work, as the hard drive died, and can't be detected. I only recently considered trying ubuntu, so I put in the live CD, and it started, although it was very slow. Wired Internet worked, but of course there was nowhere to install drivers for wifi.

When I want to connect my Xbox 360 to the internet, the only solution I have currently is to use my working laptop. In windows, I rightclick on both the wifi and ethernet, and bridge them.

Now, this isn't a great solution, because it means nobody else can use the laptop at the same time, so my family basically say I can only use it when nobody else wants to. Which is never. So it occurred to me that since I'd only need to use the ethernet port and the wifi card, I could set it up as a permanent solution to my gaming needs. Obviously a Live CD wouldn't work; it would have to be a live USB. I can easily get that sorted, but is this viable? I don't know if bridging the connections is viable in Ubuntu, but I'm sure there must be some way, considering how versatile it is.

In case it helps, my old laptop is an Inspiron 1525, with Broadcom wifi card. My new laptop (although I doubt this has any relevance) is an Inspiron 1545.

Many thanks in advance (hopefully) :)


PS - Is 'wireless bridge' the correct term? It sounded about right when I typed the title.

---

### Post by tcrowter on 2010-06-11
Forgot to mention that I haven't tried bridging any connections in Ubuntu -- so this would have to be possible before trying to actually use the laptop without a hard drive.

---

### Post by efflandt on 2010-06-11
Of course the easiest thing to do would be to use a wireless bridge or router capable if acting as a wireless client bridge.  Most routers cannot do that natively.  Many Linksys routers can using 3rd party dd-wrt firmware.  One that I have used for many years to connect my desktop, BluRay player, and sometimes on old laptop with no wireless, to my DSL wireless/modem/router is a Zyxel P-330W, which is usually economical and can natively do "wireless client bridge".  [http://us.zyxel.com/Products/Details.aspx?CategoryGroupNo=PDCA2007047](http://us.zyxel.com/Products/Details.aspx?CategoryGroupNo=PDCA2007047)

I don't think your laptop wireless would be able to work as an access point, but it could do ad-hoc wireless connections.  Although, I could be wrong about inability to be an access point.

I have never done bridging in Linux, but have done something similar using proxy_arp.  I had 3 nics on a box, one for pppoe, one for wired LAN, and one to a wireless AP.  For the wireless AP, I basically set up a 255.255.255.248 subsubnet of my main LAN 255.255.255.0 subnet.  Example:

inet addr:192.168.1.241  Bcast:192.168.1.247  Mask:255.255.255.248

That results in 5 IP's usable by other devices on that (wireless) subnet 192.168.1.242-246

I usually used network or firewall settings or scripts to enable IP forwarding, and not sure how that it typically enabled in Ubuntu, but I am guessing that it could be manually enabled or scripted by doing:

sudo echo "1" > /proc/sys/net/ipv4/conf/all/forwarding

Then assuming that eth0 is the connection to your LAN, proxy_arp would be enabled (allowing Linux to answer arp for anything connected to its other interfaces) with:

sudo echo "1" > /proc/sys/net/ipv4/conf/eth0/proxy_arp

Then suppose your xbox is 192.168.1.242 and the router on your main LAN is trying to find it with "arp who has 192.168.1.242".  Your eth0 interface would answer that it has it, and would pass the traffic on to its wireless interface.

---

### Post by tcrowter on 2010-06-12
> **efflandt said:**
> Of course the easiest thing to do would be to use a wireless bridge or router capable if acting as a wireless client bridge.  Most routers cannot do that natively.  Many Linksys routers can using 3rd party dd-wrt firmware.  One that I have used for many years to connect my desktop, BluRay player, and sometimes on old laptop with no wireless, to my DSL wireless/modem/router is a Zyxel P-330W, which is usually economical and can natively do "wireless client bridge".  [http://us.zyxel.com/Products/Details.aspx?CategoryGroupNo=PDCA2007047](http://us.zyxel.com/Products/Details.aspx?CategoryGroupNo=PDCA2007047)

I don't think your laptop wireless would be able to work as an access point, but it could do ad-hoc wireless connections.  Although, I could be wrong about inability to be an access point.

I have never done bridging in Linux, but have done something similar using proxy_arp.  I had 3 nics on a box, one for pppoe, one for wired LAN, and one to a wireless AP.  For the wireless AP, I basically set up a 255.255.255.248 subsubnet of my main LAN 255.255.255.0 subnet.  Example:

inet addr:192.168.1.241  Bcast:192.168.1.247  Mask:255.255.255.248

That results in 5 IP's usable by other devices on that (wireless) subnet 192.168.1.242-246

I usually used network or firewall settings or scripts to enable IP forwarding, and not sure how that it typically enabled in Ubuntu, but I am guessing that it could be manually enabled or scripted by doing:

sudo echo "1" > /proc/sys/net/ipv4/conf/all/forwarding

Then assuming that eth0 is the connection to your LAN, proxy_arp would be enabled (allowing Linux to answer arp for anything connected to its other interfaces) with:

sudo echo "1" > /proc/sys/net/ipv4/conf/eth0/proxy_arp

Then suppose your xbox is 192.168.1.242 and the router on your main LAN is trying to find it with "arp who has 192.168.1.242".  Your eth0 interface would answer that it has it, and would pass the traffic on to its wireless interface.

Thanks very much for your reply! I'm going to set up a USB Startup Disk today, and I'll try what you suggested. One thing of note, however, is that I didn't plan to use it as an access point. I might not have clarified exactly, so I'll just go through what I have:

Internet -> Wi-Fi Router (connected to 1 printer and 1 computer by wired) -> Laptop (via wifi) -> Xbox (via wired). This is the setup I use with windows, but I plan to use exactly the same, if I can , with ubuntu on the dead-ish laptop. Hopefully that will make it clearer :)

Also, I forgot to mention that I'm just starting with using Ubuntu fully -- managed to persuade my parents to let me install as a dual boot on one pc, and fully on an old one. It took me a while to persuade them, so I'm only just starting to get to grips with it fully. That might explain why my future replies have moronic mistakes in, etc.

Thanks very much for your help! :D

---

### Post by efflandt on 2010-06-12
I guess I was too tired when I posted earlier and got turned around explaining the proxy_arp for connecting wired to a wireless network (early long service call out in the sun).  I have done that with a laptop, and wired would be set up as a normal wireless client on the WLAN, and the ethernet would be a limited subsubnet of your LAN subnet.

And proxy_arp would instead be enabled for your wireless device on that computer.  So if your wireless is wlan0, you would enable proxy_arp by doing:

sudo echo "1" > /proc/sys/net/ipv4/conf/wlan0/proxy_arp

So you would set up the xbox with a static IP in the subsubnet like 192.168.1.242 in my example, with netmask 255.255.255.248, gateway 192.168.1.241, and whatever DNS your LAN uses.

---

