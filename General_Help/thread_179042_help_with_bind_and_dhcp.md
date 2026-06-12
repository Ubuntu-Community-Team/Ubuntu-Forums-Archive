---
title: "help with bind and dhcp"
date: 2006-05-18
forum: General Help
---

### Post by armon_d on 2006-05-18
hey guys,
I have a server with two NICS, eth0- connects to outside world and is served with dhcp, and eth1- connects to switch to serve LAN. I recently setup dnsmasq to do dhcp and dns, but it doesn't do a good job (as a DNS). I have tried bind9 and dhcp3-server, but I am sorta a newb, and had no success, even with online tutorials (these are now uninstalled). I would be extremely grateful if someone who knows how to set this stuff up would help me with a tutorial specifically for my case. I am willing to give what info is necessary for this configuration. I use ubuntu breezy on my server.

These are desired/ in place settings
Internal network 192.168.1.100-192.168.1.250, netmask 255.255.255.0
eth0- Dynamic
eth1-192.168.1.1

Please keep it some what simple (I'm a fan of webmin...)
Thats about it... Thanks in advance.

---

### Post by ProjectGod on 2006-05-19
sooo... 1 of the ethernet cards is connected to a router? and the other one is internal and static?

you want to make the internal DHCP enabled?

you want the IP address allocation to work from .100 to .250? not .1 to .250?

uh what kind of internal network setup do you have?

---

### Post by armon_d on 2006-05-19
everything you have said is correct. NOthing fancy on the inside, few printers, workstations, and another server (no impact on settings). I would have a few of the machines assigned static IP's, but that is it.

---

### Post by majastic on 2006-05-19
[QUOTE=ProjectGod]sooo... 1 of the ethernet cards is connected to a router? and the other one is internal and static?

you want to make the internal DHCP enabled?

you want the IP address allocation to work from .100 to .250? not .1 to .250?

uh what kind of internal network setup do you have?[/QUOTE]

You cant set .1 in your DHCP scope because that would be your default gateway.

---

### Post by redistributer on 2006-05-19
make sure you have the root servers file
there is distribution of linux designed just for that purpose, it's a router, e-mail server, dns server, and much more.

[http://www.clarkconnect.com/](http://www.clarkconnect.com/)

use the home edition version to test

---

### Post by armon_d on 2006-05-19
That ClarkConnect looks promising, but I'd like to stick with Ubuntu (as well as learn how to setup bind and dhcp a bit). Majastic- I didn't know that, thanks. But, I really have very little idea how to setup dhcp3-server (its not too complicated, but interoperability with bind...) , bind9 (totally lost), and how to make them work together (can't be too bad). So if you could suggest a possible configuration for me that would be greatly appreciated!

---

### Post by majastic on 2006-05-19
I know this might be a little off topic, but I'm writting this just incase to prevent a furture confusion.

As far as your configuration goes, i can help you with that, but  which programs to use, thats my n00b area. I know networking, but not so much linux...yet!
What you had setup IP wise is alright. Your eth0 port "should" be static also if you want internet traffic to flow through it without worry in the future. If you keep it DHCP, its likely to change and your eth1 to eth0 gateway will be messed up. do an *ifconfig* and find your eth0 settings and just set them static as they are from DHCP. For this example, lets just say that its 
71.97.231.240 - IP
255.255.128.0 - SNM
71.97.231.1 - DGW
71.97.200.3 - DNS1
71.97.210.2 - DNS2

The way you would have eth1 setup is
192.168.1.1 - IP
255.255.255.0 - SNM
71.97.231.240 - DGW ( gateway to eth0 IP )
71.97.231.240 - DNS1
71.97.200.3 - DNS2

The IP of eth1 can be whatever because it will be in the scope of your IP scheme. The subnet mask has to be different from eth0 or else the IP tables get all confused. The default gateway of eth1 has to be the IP address of eth0 so it will point in the right direction. DNS1 of eth1 has to be IP of eth0 for nameserver reasons. The DNS2 of eth1 should also be the DNS1 of eth0 for nameserver reasons also. After that your DHCP scope for your hosts can be whatever you want it to be from 192.168.1.2 on up. I like to give some leway and start it at around 50. Of course, your DHCP program will take care of all that for your hosts.

---

### Post by armon_d on 2006-05-19
My bridge connection in terms of log term stability is fine, as I have shorewall (a firewall) that does the configuration of that automatically. My real difficulty lies with setup of bind9 and dhcp3-server.

---

### Post by ProjectGod on 2006-05-20
armon d. 

shorewall is a good firewall but a better one i find is "**firestarter**" its got its own DHCP server implementation on it!!!

i may kind of get off the topic below here but... 

i would suggest you try and search for the right dhcp server. with "apt-cache search dhcp server" ... install and experiment.

is it a purely linux network or is it a windows / linux hybrid network? a workgroup environment with stand alone "servers" or is it a domain environment with windows active directory domain controllers???

if its just a workgroup that you wnat to try and experiement using dhcp with... try and isolate just 1 machine first and experiment with DHCP... what i mean by this is try using a crossover cable to plug one DHCP client to the ubuntu machine with two network interfaces... the former interface that was connected to the "outside" on the ubuntu machine can be temporarily configured to be a normal DHCP client for the router. however IN SAYING THIS... i'm assuming your router is a mini dhcp / dns / proxy / nat device! :)

furthermore i can imagine what youre trying to do... youre wanting to configure a firewall (ubuntu machine with 2 NICs) inside the router itself for more protection? right? if my guess is right then you could try and let another ubuntu machine on the network act as the DHCP rather than let the firewall ubuntu machine... in doing so you can let the ubuntu machine with 2 nics act solely as a router / firewall... its not very common for a firewall device to also act as the DHCP server.

hope i'm helping out. :-k

---

### Post by armon_d on 2006-05-20
[QUOTE=ProjectGod]armon d. 

shorewall is a good firewall but a better one i find is "**firestarter**" its got its own DHCP server implementation on it!!!

i may kind of get off the topic below here but... 

i would suggest you try and search for the right dhcp server. with "apt-cache search dhcp server" ... install and experiment.

is it a purely linux network or is it a windows / linux hybrid network? a workgroup environment with stand alone "servers" or is it a domain environment with windows active directory domain controllers???

if its just a workgroup that you wnat to try and experiement using dhcp with... try and isolate just 1 machine first and experiment with DHCP... what i mean by this is try using a crossover cable to plug one DHCP client to the ubuntu machine with two network interfaces... the former interface that was connected to the "outside" on the ubuntu machine can be temporarily configured to be a normal DHCP client for the router. however IN SAYING THIS... i'm assuming your router is a mini dhcp / dns / proxy / nat device! :)

furthermore i can imagine what youre trying to do... youre wanting to configure a firewall (ubuntu machine with 2 NICs) inside the router itself for more protection? right? if my guess is right then you could try and let another ubuntu machine on the network act as the DHCP rather than let the firewall ubuntu machine... in doing so you can let the ubuntu machine with 2 nics act solely as a router / firewall... its not very common for a firewall device to also act as the DHCP server.

hope i'm helping out. :-k[/QUOTE]


Here's the deal. My ubuntu machine used to just serve the purpose of ftp/web server/jabber server. But durring a power surge our router blew up ( I could never figure that out, it was on a surge protector.) And the network had to be up and running in a day. So I tried firestarter, but it was really annoying to me, and shorewall is just more advanced. Currently I have dnsmasq serving dns and dhcp, the dhcp part of it works but the dns is near useless. I have read that bind and dhcpd are the standard, but It is just to complex for me.

---

### Post by armon_d on 2006-05-21
[QUOTE=armon_d]Here's the deal. My ubuntu machine used to just serve the purpose of ftp/web server/jabber server. But durring a power surge our router blew up ( I could never figure that out, it was on a surge protector.) And the network had to be up and running in a day. So I tried firestarter, but it was really annoying to me, and shorewall is just more advanced. Currently I have dnsmasq serving dns and dhcp, the dhcp part of it works but the dns is near useless. I have read that bind and dhcpd are the standard, but It is just to complex for me.[/QUOTE]


Don't worry guys. I got the dns and dhcp working, but not really as it wouldn't serve ip addresses. So pretty much I just uninstalled everything.

---

