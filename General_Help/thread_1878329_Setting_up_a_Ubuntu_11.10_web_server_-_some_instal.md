---
title: "Setting up a Ubuntu 11.10 web server - some installation questions..."
date: 2011-11-09
forum: General Help
---

### Post by CoolBreeze47 on 2011-11-09
Hi there

I am preparing to set up a Ubuntu web server. I'm running a dual-core 64-bit machine, Ubuntu 11.10, I have a single dedicated IP address on a business account and I am following the "Perfect Server" tutorial on howtoforge but I am confused about several things. I'll list them in order...

1) In the setup it asks for a hostname and the example given is "server1.example.com". Should I use my actual domain name for this?. For example, if I wanted to name my computer "neptune", could I use "neptune.my_real_domain_name.com"?.

2) In the "Network Settings" it asks for primary and secondary DNS servers. Should I use the DNS servers provided by my ISP (the ones shown in my router), the ones provided to me by my DynDNS account or should I use my dedicated IP address here (I only have one).

3) In the "Network Configuration" screen, it asks for my "static IP address" and gives "192.168.0.100" as an example. Is this my computer's IP address or is this where I am supposed to type in my dedicated IP address?.

4) Where can I locate my "Default Gateway IP"?. Is this the same IP I use to access my router?.

5) Again, it asks for primary and secondary DNS servers. I'm not sure which DNS servers I am supposed to provide...the DNS servers provided by my ISP (the ones shown in my router), the ones provided to me by my DynDNS account or should I use my dedicated IP address here)?.

Thanks for any assistance you folks can provide. Very much appreciated.

- CB

---

### Post by papibe on 2011-11-09
Hi CoolBreeze47.

1) Short name should be fine. It can be change later anyway.
2) Either DynDNS or ISP, but not your IP.
3) If you are directly connected to the Internet, then you can use your dedicated IP, but if you are behind a router use the LAN IP (192....)
4) Usually yes. It is the address that 'goes' to the outside world (Internet).

Hope it helps,
Regards.

---

### Post by CoolBreeze47 on 2011-11-09
Thanks for the reply. I found it very helpful. Just a few follow-up questions if you don't mind and just to clarify...am I supposed to substitute the name "server1.example.com" with my real domain?. For example...

"server1" becomes "neptune" (this is what I plan to name my server).

"example.com" becomes my actual FQDN (fully qualified domain name).

So if my real domain name was perkypinkpricklypickles.com, I assume I would replace "server1.example.com" with "neptune.perkypinkpricklypickles.com". Is this correct?.

As to question 2#, I am behind a Linksys router. Which would be best to use for the primary and secondary DNS servers...DynDNS or the DNS servers provided by my ISP?.

As to question 3#, since I am behind a router and directly connected to the Internet, I guess it's safe to just use my router's IP then?.

Again, thanks!. I have actually been looking all over for this info with zero luck.

- CB

---

### Post by papibe on 2011-11-09
> **CoolBreeze47 said:**
> neptune.perkypinkpricklypickles.com
That's correct.

> **CoolBreeze47 said:**
> As to question 2#, I am behind a Linksys router. Which would be best to use for the primary and secondary DNS servers...DynDNS or the DNS servers provided by my ISP?.
Both will work just fine. In terms of initial setup it is not that important. After installation you can do some testing in order to determine which one has better response time. If the DynDNS servers need some sort of login prerequisite to function properly, I would go with your ISP's (for the installation at least).

There's a few inconveniences of not having a local DNS in the network though (not for installation). In a typical house, your router also serves as a DNS server (actually relaying requests). That is very convenient since all machines can reach each other using local names (no domains).

That may not be a problem in your network (office?). Again, can be change afterwards.

> **CoolBreeze47 said:**
> As to question 3#, since I am behind a router and directly connected to the Internet, I guess it's safe to just use my router's IP then?.
Yes.

Hope it helps. Tell us if you have more questions.
Regards.

---

### Post by CoolBreeze47 on 2011-11-09
First, I want to thank you for such a detailed and thorough reply. On a lot of these forums people answer a question with a question, take you in circles, just post a link or tell you to type in a dozen or so commands into the terminal. Your replies are actually straightforward, to-the-point and very helpful so thanks!.

The machine will just be a simple home server.

I just looked at my router settings and in the "Setup" section, "Use static IP" is selected from the drop-down menu (which is fine) but the "IP address" and "Default Gateway" forms contain my dedicated IP address rather than a "192.168..." address. I also see that the subnet mask is different than the subnet mask of my machine.

Do I go with router settings or with my machine's settings?. Here's the information I plan to use so far to set up the Ubuntu 11.10 server edition...

Hostname: neptune.mydomain.com
Name: eth1
Device: eth1
Use DHCP [] (disable)
Static IP: 192.168.0.100
Netmask: 255.255.255.0
Default Gateway IP: 192.168.0.1
Primary DNS: (from router)
Secondary DNS: (from router)

Again, the above information is primarily taken from my machine whereas the router information contains numbers that are different which is making me somewhat confused about which information I should use (ie; from router or from machine). I'm guessing I should use local IP's/subnet mask for the server setup (rather than the one's in the router)?.

NOTE: Immediately after installing the Ubuntu 11.10 server edition, I plan on running "sudo apt-get install ubuntu-desktop" or "sudo apt-get  install --without-recommends ubuntu-desktop". Will this cause any issues?. I want the server flavored kernel but I also want to make installation/configuration as painless as possible.

Thanks again.

---

### Post by papibe on 2011-11-09
In a simple network like a home network, router rules. It is all: DNS, default ruote, set masks, etc. However in an office network could be another devices or servers (for example a Windows Server) that share the network responsibilities.

Could you tell us a little bit about the network where you are installing the server?

Regards.

---

### Post by CoolBreeze47 on 2011-11-09
In my router, there is a section under "Setup" that reads "Additional information required by some ISP's". Within this same section, there are entries for the following...

* IP Address: (My dedicated IP address is shown here - not a 192.168... number)

* Subnet Mask: (This is a "255.255.255.xxx" number which is only a few digits off from my machine's subnet mask)

* Default Gateway: (My dedicated IP address is shown here as well - also not a 192.168... number)

* DNS 1: (The primary DNS number my ISP told me to use in the router)

* DNS 2: (The secondary DNS number my ISP told me to use in the router)

Are these router numbers what I should use during the Ubuntu 11.10 server installation or should I use the numbers I mentioned earlier (ie; local machine numbers)?.

My network consists of the following...

A cable modem connected to a router which connects to several other computers in the house. It's really a fairly simple setup.

Would you be able to use the template and fill in the blanks on where the information should come from (ie; machine or router). It probably sound silly but it would be very useful to me. Here's the template...

Static IP: From machine or router?
Netmask: From machine or router?
Default Gateway IP: From machine or router?
Primary DNS: From router or DynDNS?
Secondary DNS: From router or DynDNS?

Also, will installing a minimal (or even full) Ubuntu desktop after the server installation still allow me to run a server or will it do any harm?.

Again, thanks for your help!.

- CB

---

### Post by papibe on 2011-11-09
Ok. I think I understand a little better your concern. Let me explain.

Your router is two networks. The Internet, and your home LAN. So there are two set of settings. The ones you are describing are for your router to connect to the Internet. There should be another page on the router that let you preview and setup the settings on the LAN side.

Depending on your Linksys router model, it may be a simpler solution. If your router supports DHCP reservation or static IPs. That is, assigning on the router an static LAN IP (192..) to your server either based on its name or MAC address. That way you don't have to do anything special in the installation. You select, like any desktop, to use DHCP, and you end up having what you want: always the same LAN IP, and all of the others parameters set automatically (route, netmask, gateway, etc).

What is your router model?

Regards.

---

### Post by papibe on 2011-11-09
> **CoolBreeze47 said:**
> Also, will installing a minimal (or even full) Ubuntu desktop after the server installation still allow me to run a server or will it do any harm?.

Not at all. You can setup any service either on the Server Edition, any desktop/GUI on top of the Server, or the Desktop Edition itself.

It's more a question of costs, hardware, space and usability.

The server edition can run very well on machines low on hardware. You don't need even a monitor, keyboard or mouse (just the first two for the installation). Once installed, you can throw it in a closet, or the basement. The down side for beginners is that the admin is all done on the terminal using ssh.

The Desktop has more hardware requirements. You need more RAM, and a monitor always connected (may be not, but some desktops fail to boot properly because they can't initiate the graphics mode). The good thing is that the administration would be easier for a person used to a graphic environment.

Also, an interesting compromise could be accomplish by installing a light desktop version like Lubuntu, or Xubuntu.

Does that help a little?
Regards.

---

### Post by CoolBreeze47 on 2011-11-09
To give you a better idea of what I'm doing and what is confusing to me, here is the tutorial I'll actually be following when I do this (page 3#)...

[http://www.howtoforge.com/perfect-server-ubuntu-11.10-with-nginx-ispconfig-3-p3](http://www.howtoforge.com/perfect-server-ubuntu-11.10-with-nginx-ispconfig-3-p3)

And here is the part of this tutorial that I find confusing...the part where you need to configure the network interfaces. I simply have no idea what numbers to use - the ones from my local machine -or- the numbers listed in my router under "Setup" or numbers from somewhere else...
===============================
**7 Configure The Network**

  Because the Ubuntu installer has configured our system to get its  network settings via DHCP, we have to change that now because a server  should have a static IP address. Edit */etc/network/interfaces * and adjust it to your needs (in this example setup I will use the IP address *192.168.0.100*): 
 vi /etc/network/interfaces
                # This file describes the network interfaces available on your system # and how to activate them. For more information, see interfaces(5).  # The loopback network interface auto lo iface lo inet loopback  # The primary network interface auto eth0 iface eth0 inet 
address 192.168.0.100 netmask 255.255.255.0 network 192.168.0.0 broadcast 192.168.0.255 gateway 192.168.0.1
==========================================
If I only new which numbers/IP's to use, I'd be on my way to getting this installed and running.

If it's any help, my router does assign local IP's. For example, my local machine IP might be 192.168.0.102 for 3-4 days and then suddenly change to 192.168.0.105 and then a week later, some other number.

My router also has "Local DHCP Server" enabled. I do see a section in the router that has "Router" and "Local network". Not sure which one to use for setting up my server though or perhaps a combination of information from both.

- CB

---

### Post by papibe on 2011-11-10
I think I can help you a little more, if you can share your router's model. I believe that would allow me to clear some of your confusion.

Regards.

---

### Post by CrusaderAD on 2011-11-10
Check out Webmin for maintaining your server, it's free and awesome.

---

### Post by JohanLombard on 2011-11-11
Hi there all!

I'm still new to ubuntu and have been able to set up my LAMP server with Webmin and Ehcp.  My aim is to set up the server for production purposes.  It's just been a very long time ago that I have been able to set up an http server.  (And that was on Windows)

I'm capable of accessing the server via my LAN, but when I use a proxy site to access it from the outside I fail to connect to the server.  I thing my fault is related to the setup in the router to work with freedns.afraid.org.

Can anyone help us set up an easy to follow tutorial to help router, dns set-up?

Any help would be greatly appreciated.

JL

---

