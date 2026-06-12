---
title: "No Internet with Static IP"
date: 2010-06-17
forum: General Help
---

### Post by JustinAlf on 2010-06-17
I wanted to give my computer a Static IP so that I can easily connect to it from other computers: ie Mythbuntu.

This is what I did.  I set it with a static to 192.168.1.107.  My gateway is set to 192.168.1.1, and 255.255.255.0 for the subnet mask.  I'm using default settings on a Linksys wireless router.  I've rebooted several times.

Nowthen, I can connect to the computer from my laptop via the IP.  Even my Iphone can connect to the computer through that IP, so I've successfully set it's IP to static, but I cannot connect to the internet.  Is there another step I missed?  Help is greatly appreciaited.  I've searched but can not find where I went wrong here.

---

### Post by HermanAB on 2010-06-17
Howdy,

You probably forgot to set the default route.

You can view the routing table with:
$ sudo route

You can set the default route with something like:
$ sudo route add default gw 192.168.1.1 eth0

---

### Post by oneloveamaru on 2010-06-17
Wait wait, your iPhone and your Laptop also have this same IP? You can only use 1 IP per computer. If you have your iPhone, Laptop and Desktop using 107, you won't be able to browse the internet.

Hopefully I just read your post wrong!

Double check a couple things, in /etc/network/interfaces is there you should see gateway. Also make sure the correct DNS server i set in /etc/resolv.conf

No DNS, no internet. No gateway, no Internet. Check those two. They should both be 192.168.1.1 if your Linksys router is doing DNS forwarding, which it does by default.

---

### Post by JustinAlf on 2010-06-17
No, laptop and Iphone are different IP's.  I should have explained that the Desktop is on MythBuntu and that is why I need to connect to them, but I didn't want to get into frontend and backend mumbo jumbo.

I did not set a default route, I basically followed the steps found here : [http://www.howtogeek.com/howto/19541/how-to-assign-a-static-ip-to-an-ubuntu-10.04-desktop-computer/](http://www.howtogeek.com/howto/19541/how-to-assign-a-static-ip-to-an-ubuntu-10.04-desktop-computer/)

I will try that tonight and see.  I followed that guide all the way, except that I made mine 192.168.1.107 for IP of the Desktop.

---

### Post by K.J. on 2010-06-17
As onelove said, you also need to set a DNS.  Although, I have an alternate suggestion.  Linksys routers support assigning static IP addresses to MAC addresses.  You can keep your ubuntu machine on DHCP and set the router to always assign it the same IP.

---

### Post by linux-hack on 2010-06-17
you don't  rely need to assign a static ip to access you pc .. you can put it on DHCP and after that it will always get the same ip from the DHCP.. it will be more easy for you :D

---

### Post by meoconvn38 on 2010-06-17
> **JustinAlf said:**
> I wanted to give my computer a Static IP so that I can easily connect to it from other computers: ie Mythbuntu.

This is what I did.  I set it with a static to 192.168.1.107.  My gateway is set to 192.168.1.1, and 255.255.255.0 for the subnet mask.  I'm using default settings on a Linksys wireless router.  I've rebooted several times.

Nowthen, I can connect to the computer from my laptop via the IP.  Even my Iphone can connect to the computer through that IP, so I've successfully set it's IP to static, but I cannot connect to the internet.  Is there another step I missed?  Help is greatly appreciaited.  I've searched but can not find where I went wrong here.

which version are you using on :D if 8.04 <-- bad with static IP :D, later vesion you can use static IP without any prolems:guitar:

---

### Post by JustinAlf on 2010-06-17
10.04 MythBuntu, so basically a modified version of Xubuntu.  

How would one go about setting a IP for MAC address work?

---

### Post by DCGStudios on 2010-06-17
Assuming your laptop gets internet connectivity on the network, that tells us at least your modem and router are sync'd. 

If you set every other device to use DHCP, and have the 1 mythbuntu machine with a static IP, they will NEVER overlap IPs.

This would be the correct network configuration for default linksys settings..

IP - 192.168.1.107
Gateway - 192.168.1.1
Subnet Mask - 255.255.255.0
Bcast - 192.168.1.255

DNS should NOT be a problem with default settings as your ISP will provide your DNS server, Unless your using a dynamic DNS service to get around this (which complicates things).

Furthermore, posting the output of the following commands would greatly improve the chances of someone knowing whats going on..

ifconfig   -  show your IP config on your network interfaces
route -v   -  show the routing of your network
ping google.com   - establish if your DNS server is working

---

### Post by K.J. on 2010-06-17
I'm not exactly sure where it is on a linksys router, but on mine it's under network setting > dhcp reservation.

---

### Post by fragos on 2010-06-17
Assuming your computers are on a LAN behind let's say a wireless router with some wired connections you're making things more complicated than they need be. DNS only comes into play when you address out to the Internet. Leave it at whatever DCHP assigned. Behind the router on the LAN you're assigned "local IP's" which aren't visible to the Internet without the NAT that your router provides. Nothing to do here either. DCHP may not consistently assign the same IP to the same PC but there is a way around this on your LAN. Each PC has a host name which should be unique for your LAN -- you'll need to set host names yourself. Now every PC is addressable as follows: if your house name is "Geo", use "Geo.local" without quotes instead of your IP address. This definitely will work for Ubuntu but I haven't tried Windows systems with this addressing.

---

### Post by Vaphell on 2010-06-17
you need DNS servers, plain and simple. Without them you can only use IPs because there is nothing that can translate human readable addresses to their IPs. When you use autoassigned IP, router also provides the info about DNS servers. If you assign IP by hand you also need to put some DNS server in connection properties - you can find these provided by your ISP on your router status page or google a bit to find some.

the most elegant solution would be to configure the router to provide static IP to that PC using DHCP. I don't know if your linksys software allows to assign static IP to MAC address though. I installed Tomato firmware unlocking that feature and now my PC always gets the same address. You can do the same if your router model is compatible with 3rd party firmwares.
[http://gnu.univ.gda.pl/~tomasz/rysunki/tomato-static-dhcp.jpg](http://gnu.univ.gda.pl/~tomasz/rysunki/tomato-static-dhcp.jpg)

---

### Post by pricetech on 2010-06-17
Where you'll find the setting does depend on the specific model of your router, but look for something like IP Reservations or Reserved IP Addresses, or wording similar to that.  You'll need the MAC address of your computer, though your router should show it under connected clients.  You'll have to use an IP that's within the DHCP pool.

---

### Post by fragos on 2010-06-17
> **Vaphell said:**
> you need DNS servers, plain and simple. Without them you can only use IPs because there is nothing that can translate human readable addresses to their IPs. When you use autoassigned IP, router also provides the info about DNS servers. If you assign IP by hand you also need to put some DNS server in connection properties - you can find these provided by your ISP on your router status page or google a bit to find some.

the most elegant solution would be to configure the router to provide static IP to that PC using DHCP. I don't know if your linksys software allows to assign static IP to MAC address though. I installed Tomato firmware unlocking that feature and now my PC always gets the same address. You can do the same if your router model is compatible with 3rd party firmwares.
[http://gnu.univ.gda.pl/~tomasz/rysunki/tomato-static-dhcp.jpg](http://gnu.univ.gda.pl/~tomasz/rysunki/tomato-static-dhcp.jpg)

You need DNS servers for the Internet to resolve domain name addressing and those DNS servers are maintained by ISP's not you. Behind a NAT LAN you can use {host}.local addressing without a DNS. I know this to be true because that is how my network works. Obviously there are other approaches and reasons for having a local DNS but they aren't needed for a basic LAN network as we might see in a home or small business. What is suggested can work and would be a learning experience but it's prone to configuration errors.

---

### Post by pricetech on 2010-06-18
> **fragos said:**
> You need DNS servers for the Internet to resolve domain name addressing and those DNS servers are maintained by ISP's not you. Behind a NAT LAN you can use {host}.local addressing without a DNS. I know this to be true because that is how my network works. Obviously there are other approaches and reasons for having a local DNS but they aren't needed for a basic LAN network as we might see in a home or small business. What is suggested can work and would be a learning experience but it's prone to configuration errors.

I don't think he was suggesting the OP set up his own DNS servers.  I didn't read that into it anyway.  What he says is correct.  You DO have to have entries for DNS servers in order to resolve names to IPs.

The title of the post makes it pretty clear that seeing his local networks isn't the OP's concern, or at least is not the purpose of the post.

---

### Post by dcstar on 2010-06-19
> **JustinAlf said:**
> I wanted to give my computer a Static IP so that I can easily connect to it from other computers: ie Mythbuntu.

This is what I did.  **I set it** with a static to 192.168.1.107.
........

Exactly how?

---

### Post by fragos on 2010-06-19
Right click the network manager icon in the applet bar then select "Connection Information" and record the Broadcast, Subnet, Route and DNS for reuse in the next step. Right click the network manager icon in the applet bar then select "Edit Connections...", Wired tab, select Auth eth0, Edit button, IPv4 Settings, Method: Manual, Add button. You'll also need to enter the DNS servers:.

---

### Post by JustinAlf on 2010-06-22
Using the Gui in Network Connections did not work for me.  I have no idea why, but it would never change the /etc/network/interface file.  But I did have success setting it and getting everything to work, including internet, with manual terminal configuration like the one below.


> **chili555 said:**
> Certainly. However, let's clarify exactly what you are after. Are you trying to get the external IP address issued by Comcast, 76.96.xx.zz, or some such, to be constant and never changing; or are you trying to get the IP address of your MythTV server, 192.168.1.xx, or some such to be constant and unchanging. I suspect you want and need the latter. 

In case that is your objective, I suggest you go into the administartive pages of your router in a web browser, usually [http://192.168.1.1](http://192.168.1.1) and find the section for DHCP. Since your router is a wired 8-port device, it probably has a DHCP range of eight numbers. If the range is, say 192.168.1.100 to 192.168.1.107, the select an IP address outside the range of the DHCP server, for example, 192.168.1.110.

On your computer, remove Network Manager. Then, in a terminal, do:```
sudo nano /etc/network/interfaces
```Add lines to make it look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.110
netmask 255.255.255.0
gateway 192.168.1.1
```Substitute your details here. Proofread twice, save and close *nano*. Now restart networking:```
sudo /etc/init.d/networking restart
```Try it out with:```
ping -c3 www.google.com
```If you get ping returns, you are connected correctly.

Post back if you get stuck or need more help.


Only thing is, I still need to configure my system to keep this IP and connection upon restart....

---

