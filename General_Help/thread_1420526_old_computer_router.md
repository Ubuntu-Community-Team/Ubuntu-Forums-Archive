---
title: "old computer router?"
date: 2010-03-03
forum: General Help
---

### Post by koszta on 2010-03-03
Hey,
I am just wondering if there are any "borders" in capacity of Linux. 
My situation is this. I have an old computer (like 1GHz, 1 GB RAM and 60 GB HDD) and I want to use it as a Linux router. I want it to run DHCP server plus iptables firewall. It will be a DHCP server and will route traffic for like 15 other workstations. (will route 3 networks)

Does anybody have experience with this (or can you just tell by the nature of my problem) if my old computer being (relatively) slow can influence the traffic flow. I mean that the computer would just run at full load and the iptables would be slowing down the Internet connection for the clients.

I dont expect to run any GUI on the router machine...


thank you :)

---

### Post by leg on 2010-03-03
There are [router distributions]("http://distrowatch.com/dwres.php?resource=firewalls") you can try.

---

### Post by koszta on 2010-03-03
Well honestly .... i would like it to run some regular distro... I prefer real linux with all the configs I am used to. My main question is not of distribution but if such hardware can handle what I want it to...

---

### Post by cascade9 on 2010-03-03
Those specs should be fine. A friend of mine does routing with smoothwall for 2 networks on a P233. 

IMO leg is right, use a routing distro. Its easier, they are made for it. Its still 'real' linux.....

---

### Post by chewearn on 2010-03-03
I don't see any problem.  Many Linux routers ran on low power processors.

---

### Post by QLee on 2010-03-03
> **koszta said:**
> Hey,
I am just wondering if there are any "borders" in capacity of Linux. 
My situation is this. I have an old computer (like 1GHz, 1 GB RAM and 60 GB HDD) and I want to use it as a Linux router. I want it to run DHCP server plus iptables firewall. It will be a DHCP server and will route traffic for like 15 other workstations. (will route 3 networks)

Does anybody have experience with this (or can you just tell by the nature of my problem) if my old computer being (relatively) slow can influence the traffic flow. I mean that the computer would just run at full load and the iptables would be slowing down the Internet connection for the clients.

I dont expect to run any GUI on the router machine...


thank you :)

In terms of a router/gateway/firewall for a fifteen seat shop, the specs of that machine should be fine.

I see you don't want to use one of the dedicated router distros. However, one of them might make things easier for you.

I use IPCop. It has an easy browser based configuration, ability to separate wireless access from the rest of the trusted LAN and the possibility of a DMZ if you run a web server. Can use squid too. I've run it successfully on a 486 (66) with 16 MB of RAM (yes, meg) but it was slow to serve up the configuration page. I'm now running it on a P1 (166) with 128 MB.

---

### Post by juancarlospaco on 2010-03-03
I got it.

The computer is not old at all, for Linux.

You can speed up things on youre network with these.

I recently setup a WIFI Router/Server/Firewall/Gateway with an old Pentium 2 notebook.

Install the lastest Ubuntu Server on it, 
you need several network interfaces, depending your needs, wired or wireless,
if wireless check that is compatible to use it on Master Mode *(can be turned on a WIFI AP)*.

On hardware, i got in order :
-an USB to UTP extender*(can use UTP wire to extend USB)*, USB WIFI Atheros with SMA conector, a short pigtail, Kozumi WIFI amplifier 1.000 mWatts, SMA Tee divisor, 2 short pigtails, 2 Omni 17dbi OutDoor antenna. 

And it got installed and configured:
-OpenSSH-Server, DHCP3-Server, Bind9 DNS Cache working with OpenDNS, Squid WebCache 10Gb cache,
UFW firewall, NTP-Server, eth0/eth1 Bonding fail-tolerance load balance 200Mb/s,
APT-Mirror-NG network Ubuntu repo working without touching clients sources.list,
Virtual LANs, Quagga Routing Suite with OSPF similar to Cisco, AppArmor Hardenning,
ETCKeeper, Automatic Security Updates, Reduced bandwith APT config for the Server itself, Munin Monitoring,
CoovaChilli WIFI Captive Portal/Walled Garden with Bandwith Limit, WPA security.

I dont give you a tutorial link because i dont use any, 
i use several documentations of each proyect.
You need time and I+D Lab ;)
Make tarball backup of your /etc when finished, if someday the disk die, you can replace it within 1 hour.

Topology:
Internet_aDSL-----Switch------Server/APwifi))) ) )  )
[COLOR="White"]_________________[/COLOR]`-----------'   
                      

:)

---

### Post by koszta on 2010-03-03
NICE JOB juancarlospaco! Thanks for sharing :) Your topology is somewhat similar to what I will be using and doing. I also plan to set up a few typical services... I am also using this real-settings case for my bachelor thesis work. My main concern is security. 

That's why I dont want to use some router distro. Want to do my work in the command line (I cant say in my bachelor thesis that I "clicked this " and it "did that"). I have configured most of the services that you talk about but not simultaneously :) I also want to make sure they are as secure as it gets. Thanks :)

---

### Post by doas777 on 2010-03-03
also check out pfsense. it's a NetBSD router distro, that you can do completely from cli if you like. rocksolid, fast, and most of the features you could want.

---

### Post by juancarlospaco on 2010-03-03
> **koszta said:**
> NICE JOB juancarlospaco! Thanks for sharing :) Your topology is somewhat similar to what I will be using and doing. I also plan to set up a few typical services... I am also using this real-settings case for my bachelor thesis work. My main concern is security. 

That's why I dont want to use some router distro. Want to do my work in the command line (I cant say in my bachelor thesis that I "clicked this " and it "did that"). I have configured most of the services that you talk about but not simultaneously :) I also want to make sure they are as secure as it gets. Thanks :)

I think i will write it with photos on the Ubuntu Wiki before heavy testing.

Not to FUD, but with other Linux/BSD Router Distros, even Vyatta,
i dont feel better or easier to perform the same deployment, 
because of customization i think, and because its a Server too *(router!=server)*.

I think is right that you say, because real routers are used by command line.
And everything was via APT, not compile, or SVN/CVS/whatever,
but i know that other Commercial routers cant do the same task as this old lappy.

BTW i never liked to use a Custom distro "ready-to-run" for any task, 
its better to use the common supported base of Ubuntu,
i feel the other are like using an unnatendded Windows instead of Windows Server.
:)

---

### Post by n8bounds on 2010-03-03
Shorewall is amazing, once you are familiar with the configuration files. 
[http://www.shorewall.net/](http://www.shorewall.net/)
It's a lot simpler than configuring IP tables directly anyway! There's plenty of good documentation on their website and packages for shorewall in the official repos.

---

### Post by koszta on 2010-03-03
> **juancarlospaco said:**
> I think i will write it with photos on the Ubuntu Wiki before heavy testing.

Not to FUD, but with other Linux/BSD Router Distros, even Vyatta,
i dont feel better or easier to perform the same deployment, 
because of customization i think, and because its a Server too *(router!=server)*.

I think is right that you say, because real routers are used by command line.
And everything was via APT, not compile, or SVN/CVS/whatever,
but i know that other Commercial routers cant do the same task as this old lappy.

BTW i never liked to use a Custom distro "ready-to-run" for any task, 
its better to use the common supported base of Ubuntu,
i feel the other are like using an unnatendded Windows instead of Windows Server.
:)
Man I couldn't agree with you more... 
The reason why I want "a real distro" is exactly why people say I should get specialized distros. I DO NOT WANT any other approach to config files. I already know general debian/Red Hat approach. Dont want to learn a new one. Even if it is easier! That is a bug not a feature. I love GNU/Linux and Unix cause it keeps standards. Oh and the package management is a great help too. I dont want to compile every crap myself. That takes forever. I am ok with some compiling BUT... As for using CLI I prefer that above any http-based control. I have had TERRIBLE experience with samba swat. I use it with Cisco devices and my other *nixes & Unixes I work with. 

I will also surely create some sort of output from my topology... Will put it online (probably just a pdf cause of the origin of my work). 

As for comercial vs linux the only comparison that is worth it is linux vs. cisco in networking... Honestly - Cisco is a little better. Easier config for the most part and more options to go with. BUT YOU PAY WITH YOUR PANTS FOR THEIR STUFF!!! :D

---

### Post by juancarlospaco on 2010-03-03
TBH Quagga has the same sintax as Cisco IOS, this is because i recommend it to you.
BTW im CCNA
:)

---

### Post by koszta on 2010-03-04
lol I only took a CCNA-like class. So techinicaly I know all I need to know for a CCNA but right now dont have the time (nor money :D) to pay and do that. Definitely plan on doing that tho.

---

### Post by QLee on 2010-03-04
> **koszta said:**
> NICE JOB juancarlospaco! Thanks for sharing :) Your topology is somewhat similar to what I will be using and doing. I also plan to set up a few typical services... I am also using this real-settings case for my bachelor thesis work. My main concern is security. 

That's why I dont want to use some router distro. Want to do my work in the command line (I cant say in my bachelor thesis that I "clicked this " and it "did that"). I have configured most of the services that you talk about but not simultaneously :) I also want to make sure they are as secure as it gets. Thanks :)

I wish you had mentioned this at the outset, koszta. I thought you were a sys admin looking for an enterprise solution and most sys admins don't need more work to do. I wouldn't have bothered writing about a useful solution if I had known you were asking for help with "homework". By the way, most people would choose something more like Debian (stable, lenny) to create a firewall/router/gateway in a production environment.

---

