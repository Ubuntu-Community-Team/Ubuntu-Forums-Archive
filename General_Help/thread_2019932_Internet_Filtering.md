---
title: "Internet Filtering"
date: 2012-07-07
forum: General Help
---

### Post by jacobroecker on 2012-07-07
I've got a ubuntu box I'd like to configure as a gateway/dhcp server for all of the users on my network and replace the router I'm using.  The final version I'm going for is a system that issues out IP addresses, but blocks internet access to all but four MAC addresses.

What software would I need to do this and how would I configure it?

Obviously the DHCP server app is a must, but what else do I need?  Google searches lead me to squid, but I haven't seen anyone try to configure it the way I need it to run.

Thanks in advance.

---

### Post by zero2xiii on 2012-07-07
Hay,

Yes squid will be your first stop.

You will set up a proxy server ON the "server". Passing all network traffic through. Then on the same server, DHCP. Then you might want to play with the routing tables to allow or deny access the internet based on MAC adressing. Squid might support this but I am unsure. See the manuals and other reference material for that.

See the following for more information:

[https://help.ubuntu.com/12.04/serverguide/squid.html](https://help.ubuntu.com/12.04/serverguide/squid.html)
[http://www.makeuseof.com/tag/set-proxy-server-ubuntu-linux/](http://www.makeuseof.com/tag/set-proxy-server-ubuntu-linux/)
[https://help.ubuntu.com/community/Squid](https://help.ubuntu.com/community/Squid)

Good luck, but might I recommend [routerOS]("http://www.mikrotik.com/software.html#")... There is another complete linux OS that is MADE for what you want to do. But I can't on the name now. Will have to dig deep to find the name. But it worked excellent as far as I can remember.

GOod luck
Cherz

---

### Post by zero2xiii on 2012-07-07
Hay,

Seems like it is not a linux distro as such (i know there is one, I wanted to use it for a wifi hotspot. But I don't find it.)

[http://www.vyatta.com/download/trial_software](http://www.vyatta.com/download/trial_software)

Cherz

EDIT:

I did however find this:

[http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.telenet.be/mydotcom/howto/lanconnect/router/linux.htm)
[http://lartc.org/howto/](http://lartc.org/howto/)

This might point you into a better direction.

---

### Post by jacobroecker on 2012-07-07
Thanks all.  It's going to be a couple of weeks before I have this machine freed up from its current workload and can test these configs.  Looks to me like you've recommended the right amount of reading for me to peruse during that time and it should make the whole process much easier.

Happy to read any other insights if anyone's got them and looking forward to this new experiment!

---

### Post by SeijiSensei on 2012-07-07
You don't really need Squid for this task, especially if your intention is to block all external connections from the unprivileged machines.  Squid only handles Web browsing; it wouldn't block a Bittorent connection or connections to a remote mail server, for instance.

For a robust solution you're much better off using iptables.  First, you'll need to set up the DHCP server to assign pre-designated IP addresses to the clients with the MAC addresses you wish to allow.  You do the with the "host" directive in [dhcpd.conf]("http://linux.die.net/man/5/dhcpd.conf").  For simplicity, let's suppose you only want to permit one machine to connect to the Internet and block everyone else.  Set up dhcpd to give the permitted machine a specific IP address, say, 192.168.1.100.  Then you would add these iptables rules on the router:

```

/sbin/iptables -A INPUT -s 192.168.1.100  -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j REJECT

```

That's it.  Now the permitted machine has full access to the Internet, and everyone else has none.  You can create more subtle policies by using rules based on ports.  For instance, here are some rules that let the privileged machine browse the Web using both HTTP and HTTPS but nothing else.

```

/sbin/iptables -A INPUT -p tcp -s 192.168.1.100 --dport 80  -j ACCEPT
/sbin/iptables -A INPUT -p tcp -s 192.168.1.100 --dport 443 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j REJECT

```

You can also specify machines by MAC address in iptables; see "man iptables" for details, specifically the "mac" match extension and its associated "--mac-source" parameter.

Finally, here's a useful rule to block things like torrents and streaming video, but enable other types of services.  It takes advantage of the fact that most any such service runs on "unprivileged" ports above 1023.

```

iptables -A INPUT -p tcp --sport 1024:65535 --dport 1024:65535 -j REJECT
iptables -A INPUT -p udp --sport 1024:65535 --dport 1024:65535 -j REJECT

```

---

### Post by Cheesehead on 2012-07-07
> **jacobroecker said:**
> I'd like to configure as a gateway/dhcp server for all of the users on my network and replace the router I'm using.  The final version I'm going for is a system that issues out IP addresses, but blocks internet access to all but four MAC addresses.

Lots of tutorials out there. Try one in a VM before doing it for real. You can prevent a lot of painful mistakes by experimenting in a VM first.

On most small networks I use:
dnsmasq (DNS and DHCP)
hostapd (Wireless LAN hotspot)
bridge-utils (Bridging wired and wireless LAN interfaces)
iptables (Firewall)
pppoe (WAN connection)

dnsmasq can easily be configured to assign IP addresses to specific MAC address clients, and IPtables can easily be configured to allow only specific MAC addresses...
...assuming the MAC addresses are not spoofed.

---

### Post by jacobroecker on 2012-07-08
> **SeijiSensei said:**
> You don't really need Squid for this task, especially if your intention is to block all external connections from the unprivileged machines.  Squid only handles Web browsing; it wouldn't block a Bittorent connection or connections to a remote mail server, for instance.

For a robust solution you're much better off using iptables.  First, you'll need to set up the DHCP server to assign pre-designated IP addresses to the clients with the MAC addresses you wish to allow.  You do the with the "host" directive in [dhcpd.conf]("http://linux.die.net/man/5/dhcpd.conf").  For simplicity, let's suppose you only want to permit one machine to connect to the Internet and block everyone else.  Set up dhcpd to give the permitted machine a specific IP address, say, 192.168.1.100.  Then you would add these iptables rules on the router:

```

/sbin/iptables -A INPUT -s 192.168.1.100  -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j REJECT

```

That's it.  Now the permitted machine has full access to the Internet, and everyone else has none.  You can create more subtle policies by using rules based on ports.  For instance, here are some rules that let the privileged machine browse the Web using both HTTP and HTTPS but nothing else.

```

/sbin/iptables -A INPUT -p tcp -s 192.168.1.100 --dport 80  -j ACCEPT
/sbin/iptables -A INPUT -p tcp -s 192.168.1.100 --dport 443 -j ACCEPT
/sbin/iptables -A INPUT -s 192.168.1.0/24 -j REJECT

```

You can also specify machines by MAC address in iptables; see "man iptables" for details, specifically the "mac" match extension and its associated "--mac-source" parameter.

Finally, here's a useful rule to block things like torrents and streaming video, but enable other types of services.  It takes advantage of the fact that most any such service runs on "unprivileged" ports above 1023.

```

iptables -A INPUT -p tcp --sport 1024:65535 --dport 1024:65535 -j REJECT
iptables -A INPUT -p udp --sport 1024:65535 --dport 1024:65535 -j REJECT

```

This method makes the most sense to me, but that doesn't mean I quite understand how to implement it.  I've never messed with IP tables before and I'm going to need some help with the code for all of this. 

Let me see if I understand this right:

I'm going to need to edit the host config of dhcpd.conf so it assigns specific IPs to specific MAC addresses that I want to have internet access.  These will be 192.168.1.40, 192.168.1.41, 192.168.1.42.  The remaining DHCP addresses need to be assigned between 100-200 to mirror the current setup.

On the ubuntu machine I'm going to set up a bridge between the two ethernet devices eth0 and eth1.  eth1 will be used for the internet side of the connection with a static IP of 10.0.4.25 and a subnet of 255.255.252.0 and a router IP of 10.0.4.1  

My current router ip is 192.168.1.1 but the ubuntu machine is also operating as a webserver off my LAN and users access it via 192.168.1.5  Since the ubuntu machine will be taking over as assigning the DHCP addressing would I change the dhcpd.conf file to identify the router as 192.168.1.5 or would I change the IP of the ubuntu machine to 192.168.1.1 and tell my users about the address change?  Would I make these changes by right clicking on the network interface icon and selecting "edit connections" or would I do this via a .conf file?

The very last request for the DHCP file is to mirror the current setup and how my router sends a message to all the DHCP users once they are connected.  I would like to send a similar message but don't know how to configure that (if I can) within the dhcpd.conf file.

Would someone mind posting the code for the dhcpd.conf and interfaces files that corresponds to my goals so I can check my work before I implement it?

The next part of this is setting up the IPTables.  After doing a brief few google searches and coming across some rather lengthy documents I've realized I'm going to need some help with this area as well.  It appears to me that IP tables are programmed using terminal and are set up on a per-boot basis.  I also understand that there are ways of saving and reloading these tables but there's no default method of doing it with a .conf file.  Some of the documentation regarding the best way of starting and saving iptables is rather old and I'm hoping someone would recommend an up-to-date standardized (if there is one) method of accomplishing this.

Since I'm new to using command line and code I prefer to edit using gedit and would love to sit in a gedit window and configure the suggested IP tables.  I've read though, that such a method is a bad idea.  

Sorry to be a bother folks.  I'm going to need some more direction on IP Table configuration and best practices.  Call me lazy, but I really didn't feel like reading this book ([http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html](http://www.frozentux.net/iptables-tutorial/iptables-tutorial.html)) to find the answer and I'm not familiar enough with some of the technical terms to be able to skim through it for exactly what I need.

Can I break this setup into stages and do the dhcpd.conf first and have it allow all the users to access the internet (that way I can test that portion) and then setup the iptables?

Lots of questions.  I promise I'm taking notes so I wont forget.  Thanks in advance!

---

### Post by SeijiSensei on 2012-07-09
> **jacobroecker said:**
> I'm going to need to edit the host config of dhcpd.conf so it assigns specific IPs to specific MAC addresses that I want to have internet access.  These will be 192.168.1.40, 192.168.1.41, 192.168.1.42.  The remaining DHCP addresses need to be assigned between 100-200 to mirror the current setup.

Here's my extremely simple dhcpd.conf without any host reservations for my 192.168.100.0/24 network:

```

ddns-update-style interim;
ignore client-updates;

subnet 192.168.100.0 netmask 255.255.255.0 {

        range 192.168.100.50 192.168.100.99;
        option routers              192.168.100.1;
        option subnet-mask          255.255.255.0;
        option domain-name          "example.com";
        option domain-name-servers  192.168.100.1, 8.8.8.8, 4.4.4.4;

         # you may not need any of the following
        option time-offset           -18000; # US Eastern
        option ntp-servers           192.168.100.1;
        option netbios-name-servers  192.168.100.1;
}

```

You would add a host reservation like this:

```

host junes_pc {
      hardware ethernet 00:00:aa:bb:cc:dd;
      fixed-address 192.168.1.37;
}

```

You insert these inside the "subnet {}" declaration.

> On the ubuntu machine I'm going to set up a bridge between the two ethernet devices eth0 and eth1.  eth1 will be used for the internet side of the connection with a static IP of 10.0.4.25 and a subnet of 255.255.252.0 and a router IP of 10.0.4.1

No, you won't be using bridging.  (I've build networks, routers, and servers for almost 20 years now; I've never used bridging.)  What you really want is to use iptables to create a router that uses "network address translation" or "NAT".  You set up a rule in iptables that uses the MASQUERADE target.  Packets arriving from the internal network with external destinations are rewritten by iptables with the router's external address inserted as the packet's source address.  The NAT code keeps track of all these rewritten packets so it can send back any replies to the originating machine behind the router.  A Google search for "iptables nat" will bring up lots of help.

> My current router ip is 192.168.1.1 but the ubuntu machine is also operating as a webserver off my LAN and users access it via 192.168.1.5  Since the ubuntu machine will be taking over as assigning the DHCP addressing would I change the dhcpd.conf file to identify the router as 192.168.1.5 or would I change the IP of the ubuntu machine to 192.168.1.1 and tell my users about the address change?  Would I make these changes by right clicking on the network interface icon and selecting "edit connections" or would I do this via a .conf file?

First, if the Linux box is replacing the router, then it makes sense for it to have the same address as the old router did.  So, yes, assign 192.168.1.1 to the LAN-facing interface on the Linux box.  The externally facing interface will be assigned an address in the subnet of the router it talks to upstream.  If this box is directly connected to the Internet, that will be an IP address assigned by the ISP either statically or via DHCP depending on how your Internet service is configured.

You don't need to tell the clients anything about this.  Client workstations simply broadcast a request for DHCP configuration information by sending a packet to the "all-ones" address, 255.255.255.255.  The DHCP server listens for these requests and replies to any it detects.  This all happens transparently without any involvement on the user's part.

> The very last request for the DHCP file is to mirror the current setup and how my router sends a message to all the DHCP users once they are connected.  I would like to send a similar message but don't know how to configure that (if I can) within the dhcpd.conf file.

I don't either, and it seems pretty superfluous to me.  Either the machine gets an address and can connect to the network, or something goes wrong and it cannot.  I've never seen any arrangement where there is some kind of additional announcement that an address has been assigned.  The networking software on the client PC may provide such an announcement, but that message wasn't sent by the DHCP server.

> The next part of this is setting up the IPTables.  After doing a brief few google searches and coming across some rather lengthy documents I've realized I'm going to need some help with this area as well.

No one said this would be easy, but it isn't really all that hard either.  Expect to invest a couple of days learning what you'll need to know.  There are lots of guides out there, but I think [this one]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables#Masquerading_.28Many_to_One_NAT.29") is comprehensive and fairly clear.  It addresses some of your other iptables-related questions.

> Since I'm new to using command line and code I prefer to edit using gedit and would love to sit in a gedit window and configure the suggested IP tables.  I've read though, that such a method is a bad idea. 

It doesn't matter what editor you use.  Ultimately all these configurations files are just plain text.  You can use gedit, emacs, vim, nano, whatever, to create them.
> Call me lazy, but I really didn't feel like reading this book

Well you are going to have to invest some time and effort into this.  As I said expect to spend a few days playing with configurations, testing them out, fixing the problems, and so forth.  If that's more effort than you have available, you might want to consider whether you should be taking on this project.

> Can I break this setup into stages and do the dhcpd.conf first and have it allow all the users to access the internet (that way I can test that portion) and then setup the iptables?

Yes, you can set up dhcpd.conf first (which shouldn't take more than an hour or so if you just adapt the simple file I posted above), but your users won't be able to access the Internet until you set up iptables and NAT.  Might I suggest building a little test network with the Linux box connected to the office LAN on the external side and connected to a single client PC on the other.  Once you get that working, so that the client PC can see the office network, you'll be ready to move on to the real thing.

People here are very helpful, but no one's going to hold your hand throughout this process.  Come back to us when you're stumped, and we'll do our best to help.

---

