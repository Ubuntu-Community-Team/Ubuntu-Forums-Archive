---
title: "Network printer problem"
date: 2010-04-16
forum: General Help
---

### Post by cmcanulty on 2010-04-16
Our library has a Ubuntu print server desktop and several laptops that use it also. Every few days to hours it stops working and I am beginning to suspect cups gets disconnected randomly but that's just a guess. Is there a terminal command I can do to never stops cups connection? Or any other ideas? It is a HP Laserjet 2100M

---

### Post by 666f6f on 2010-04-16
I will assume that by "stops working" you mean that the print server computer is still up and running but it does not print documents.

1. Can you successfully ping the print server?
2. Can successfully connect to port 631 (or whatever port your CUPS server listens to) of your print server via telnet?
3. Have you checked /var/log/cups logs for anything suspicious?

---

### Post by cmcanulty on 2010-04-16
I will be at library Monday eve and will try those ideas, lib is closed now for weekend, thanks

---

### Post by hawthornso23 on 2010-04-17
Is this a network printer or a printer shared across a network.

If it is a network printer then the problem could be that the IP number of the printer is being set by DHCP and is changing. That can be fixed by assigning the printer a static IP on the network. It is also possible to install a network printer via its WINS name.

---

### Post by cmcanulty on 2010-04-17
Can you explain how to do that? That would explain the intermittent nature of the problem.  I may have done that at one time but forget how. Would that work with a dynamic internet address for the whole network? We can't have a static ip address as it is much more expensive.Thanks.

---

### Post by hawthornso23 on 2010-04-17
I am talking about the IP address of the printer on the local network changing, not the IP address assigned when you go out on teh internet.. 

Computers on a local network each have a local IP address - which follows one of the patterns  192.168.*.*  or  10.*.*.*   reserved for local networking.  These local IP addresses are usually assigned by a protocol called DHCP. When it is turned on a device on a local network sends out a broadcast requesting an IP address. A DHCP server on the network (often the router) assigns it a vacant IP address. This means that local IP addresses change every now and then as devices are turned on and off.

To assign the printer a static IP address you need to access the DHCP server and tell it to reserve a particular IP address for the printer. If a computer on the network is acting as DHCP server you need to log onto that machine to do this. If a router is acting as DHCP server you need to log into the router which you can do by typing its local IP address into a web browser. You'll need to login in with name and password.

If the router hasn't had its IP address, login name and password changed then they will be manufacturer's defaults and the values depend on the make of the router - try variations on the theme of 10.1.1.1 or 10.0.0.0 or 192.168.0.1 for the IP address, admin for the login name, and blank (or `password') for the password. Once you get in, the interface is usually pretty self explanatory.

If this isn't your network and/or you can't access the DHCP server then you can't set a static IP address for the printer. In that case you'll have to teach your ubuntu how to use WINS so that it can access the printer by name (which is what the winblows computers do). WINS is a protocol for attaching computer names to IP addresses on the local network. That is done by a WINS server - a kind of directory service - once again usually the router unless another machine has been set up to do this job. 

WINS is installed as part of samba, so if you've installed samba you'll have it. Otherwise you'll have to install it via synaptic. You'll know you've got WINS installed if you can ping computers on the local network by name. It isn't part of the default ubuntu installation.
[COLOR=Red]
[/COLOR][COLOR=Red]**EDIT: **[/COLOR][COLOR=Red]Oops forgot something. You've also got to add wins to your /etc/nsswitch.conf file to tell ubuntu to use WINS when looking things up. Edit this file by sudo. Look for the line that starts `hosts'. You'll see a list of things. Add `wins' to the list just before where it says dns. For example mine now says[/COLOR]

hosts:          files mdns4_minimal [NOTFOUND=return] [COLOR=Red]wins[/COLOR] dns mdns4
[COLOR=Red]
Just add wins - don't make other changes or you could break your ubuntu. Your hoists line may look different depending on what else you've got installed.[/COLOR]

To install a network printer by name you need to know its name. If this is a library they may have documentation that lists it. If you can login to the router, it'll tell you the names of connected devices. Or you can login to the printer itself (type its IP address into a web browser) and find out there. The printer may need a login name and password which once again will be manufacturer's defaults (unless changed).

To install a printer by name, go through the usual procedure of installing a network printer. It'll find the network printer for you and suggest something like  

socket://10.1.1.5:9100

Just replace the IP number part with the WINS name of your printer - eg -

socket://BRN_7D2A6F:9100

and hit return. It'll ponder briefly (while it checks that this works) and if it can find the printer using that name it'll install and access in future via WINS name. This means you won't have to reinstall every time the IP address changes.

Good luck.

These instructions are all for a NETWORK PRINTER - one directly connected to a network and not just connected to a computer and then shared across a network. If the printer is plugged directly into the network via an RJ45 cable then you have a network printer. If it is connected to another computer via a USB or LPT cable then you have a printer which is shared across a network which is a very different beast.

---

### Post by cmcanulty on 2010-04-18
OK the printer is hooked up to a desktop computer and shared through the network. I earlier tried just using ethernet to the wall outlet and had no luck finding it anywhere. So I think hooking up to the computer is the way to try, any advice on that? Thanks again

---

