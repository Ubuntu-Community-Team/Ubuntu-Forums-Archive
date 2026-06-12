---
title: "What is DHCP protocole?"
date: 2006-05-02
forum: General Help
---

### Post by SwaroopKunduru on 2006-05-02
Hi All,

When installing UBUntu as dual boot I am getting the message that the system is not using DHCP protocole so configure the system to use DHCP. If I install completly does it work fine? If i boot windows does it work?

Please help.

Thanks and Regards,

---

### Post by PhoenixP3K on 2006-05-02
DHCP has to do with the network connection you use. DHCP is when the router or modem assigns an IP address to your computer so it can access the network (or Internet) if you don't have DHCP enabled you might have to configure your IP manually. What kind of internet access do you have and what kind of hardware do you have ? Router or direct modem connection ?

---

### Post by physcsdrk on 2006-05-02
If you are not using a third party router, then the fastest way to figure out how to configure your internet connection is to call your isp's tech support.  Just tell them you want to know what protocol you have and how that protocol authenticates.  If the person stumbles through the explanation, ask for a supervisor so they don't muck it up.  

DHCP uses your mac address to authenticate with your isp.  If you are not dhcp and you are not using a router most likely you are PPPoE or something like that and you authenticate with your username and password from your isp.  If you don't know those things make sure you get them from tech support.

btw, things having to do with your protocol aren't going to stop you from booting into windows.

---

### Post by SwaroopKunduru on 2006-05-02
Hi PhoenixP3K and Physcsdrk,

I have comcast cable internet and I have Netgare wireless router My laptop has wireless Netgare adaptor. On windows I had installed Netgare driver. Do you have any Idea I can fix my internet connection.

Regards,

Swaroop kunduru.

---

### Post by PhoenixP3K on 2006-05-02
Under Ubuntu you can try to change your network settings
**System -> Administration -> Networking**
[IMG]http://easylinux.wordpress.com/files/2006/04/Network%20-%202%20-%20Cards.png[/IMG] and then you must activate and edit the proprieties of the Wireless card. If you are not using the wired Ethernet cable you might as well disable "Ethernet Connection"
So assuming that your Netgear adaptor is a kind of wireless card you click on Proprieties and should see something like this. [IMG]http://easylinux.wordpress.com/files/2006/04/Network%20-%204%20-%20Wired%20Settings.png[/IMG]
Then try selecting DHCP. You should also double check the user guide that came with your Router to see if it has DHCP enabled by default. 

On the other end! If the Netgear adaptaor you're talking about is an Ethernet bridge (wire that goes to the adaptor) you should leave the Ethernet connection and edit those proprieties as well.

If you have to assign a specific IP address it might be a little more complicated because I don't know what settings Netgear hardware use nor what DNS Comcast has. So pray that enabling DHCP works... (it should of detected during the install... I'm sure you have to activate it in your router)

*Special thanks to [Linux for human beings?]("http://easylinux.wordpress.com/2006/04/29/networking-in-dapper-drake-beta/") for the screenshots already available from it's post on configuring a network under Ubuntu Dapper.* Might help you.

---

