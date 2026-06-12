---
title: "Good Firewall / Monitoring Software"
date: 2010-01-22
forum: General Help
---

### Post by Overcast32 on 2010-01-22
Anyone know of any good Firewall / Monitoring software for Linux out there? Would prefer something that works good with Ubuntu.

At best, I would like something that could get 'blacklists' from the web to restrict various types of content, of course I realize that's like 'enterprise level' type of stuff. But I've seen some great open source stuff. 

I really need it to be able to track what sites are being accessed in close to real time and give me options to block any domain I choose. 

I am looking at using an Ubuntu machine as a 'gateway' between my Cable Modem and Router - so it can filter all traffic coming across the network. 

Any suggestions? :)

I'm not adverse to paying, but I would need to demo it at first.

---

### Post by OnlyTim on 2010-01-22
Hi Overcast, I'm still a newbie, but I've completely switched to Ubuntu from windows now and wasn't sure about giving up my Nortons. After a few months I found Firestarter, a nice GUI firewall that can be found on the Ubuntu software center that you can manipulate. I can lock the firewall when working off line and control port access. It logs all intrusion, either normal or unknown. What it considers serious, it highlights in red in the events tab. 

So far, I'm happy with it.

Cheers

---

### Post by doas777 on 2010-01-22
I haven't yet found one. I had used firestarter, but it is old and out of date, so most folks recomend gufw instead. gufw however does not have any monitoring components  and the way it handles port ranges is just plain stupid (writes 1 rule per port, so can take hours and hours to apply a new rule set).

if you find somthing kewl let us know.

---

### Post by Overcast32 on 2010-01-22
Thanks for the quick replies, my core focus is monitoring. Not that I really want to - by my young daughter's went a bit 'too far' with some issues and I need something to restrict what she can and can't do - that or just cut her access altogether. 

Will Firestarter block domains? I think that's my main focus. I guess if nothing else, I can use some DNS trickery.

---

### Post by pirateghost on 2010-01-22
> **Overcast32 said:**
> Thanks for the quick replies, my core focus is monitoring. Not that I really want to - by my young daughter's went a bit 'too far' with some issues and I need something to restrict what she can and can't do - that or just cut her access altogether. 

Will Firestarter block domains? I think that's my main focus. I guess if nothing else, I can use some DNS trickery.
why not try out one of the dozens of linux-based/bsd-based router/firewall distros?

have a look at pfsense, untangle, vyatta (if you want a strict commandline experience), smoothwall

those will pretty much do all those things.  and they are easy to set up (aside from vyatta, it has a nice learning curve)

---

### Post by teresaejunior on 2010-01-22
You don't need to install anything to get firewall and monitor your connections.

I use a small script to start a firewall in less than half a second:

```
#!/bin/sh

# Flush all rules
iptables -F
iptables -X

# Setting default filter policy
iptables -P INPUT DROP
iptables -P OUTPUT ACCEPT
iptables -P FORWARD DROP

# Allow unlimited traffic on loopback
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# allow input to only outgoing connection like DNS queries
iptables -A INPUT -i ppp0 -m state --state ESTABLISHED,RELATED -j ACCEPT
```

This gives a perfect result in firewalls testing (100% stealth)!

And you can get a list of open connections with the command "netstat --inet" in a terminal, which works like Microsoft Tcpview, example output is (in my locale language) :

```
Conexões Internet Ativas (sem os servidores)
Proto Recv-Q Send-Q Endereço Local          Endereço Remoto         Estado     
tcp        0      0 37.122.47.187.isp:38887 feijoa.canonical.co:www ESTABELECIDA
tcp        1      0 37.122.47.187.isp:38906 feijoa.canonical.co:www ESPERANDO_FECHAR
tcp        0      0 37.122.47.187.isp:46008 lga15s04-in-f104.1e:www ESTABELECIDA
tcp        1      0 37.122.47.187.isp:45995 lga15s04-in-f104.1e:www ESPERANDO_FECHAR
tcp        0      0 37.122.47.187.isp:38905 feijoa.canonical.co:www ESTABELECIDA
tcp        1      0 37.122.47.187.isp:46005 lga15s04-in-f104.1e:www ESPERANDO_FECHAR
tcp        0      0 37.122.47.187.isp:47459 qw-in-f139.1e100.ne:www ESTABELECIDA
tcp        0      0 37.122.47.187.isp:38894 feijoa.canonical.co:www TIME_WAIT  
tcp        0      0 37.122.47.187.isp:38898 feijoa.canonical.co:www ESTABELECIDA
tcp        1      0 37.122.47.187.isp:46006 lga15s04-in-f104.1e:www ESPERANDO_FECHAR
tcp        0      0 37.122.47.187.isp:38897 feijoa.canonical.co:www ESTABELECIDA
tcp        1      0 37.122.47.187.isp:38900 feijoa.canonical.co:www ESPERANDO_FECHAR
tcp        1      0 37.122.47.187.isp:38903 feijoa.canonical.co:www ESPERANDO_FECHAR
tcp        0      0 37.122.47.187.isp:46007 lga15s04-in-f104.1e:www ESTABELECIDA
tcp        0      0 37.122.47.187.isp:41272 72.14.204.101:www       ESTABELECIDA
tcp        1      0 37.122.47.187.isp:38901 feijoa.canonical.co:www ESPERANDO_FECHAR
tcp        1      0 37.122.47.187.isp:46004 lga15s04-in-f104.1e:www ESPERANDO_FECHAR
tcp        1      0 37.122.47.187.isp:38907 feijoa.canonical.co:www ESPERANDO_FECHAR
tcp        1      0 37.122.47.187.isp:38902 feijoa.canonical.co:www ESPERANDO_FECHAR
tcp        1      0 37.122.47.187.isp:38904 feijoa.canonical.co:www ESPERANDO_FECHAR
tcp        0      0 37.122.47.187.isp:38899 feijoa.canonical.co:www ESTABELECIDA
tcp        0      0 37.122.47.187.isp:43946 yo-in-f101.1e100.ne:www ESTABELECIDA
```

This is what i found about blocking a domain with iptables and using the netstat command:

```
u'll have to use ips and if u'd like to block all DOMAIN names u can these just replace where needed.

iptables -A OUTPUT -p all --destination 127.0.0.1 -j DROP

find out the ip of a domain name and then find out it's whole ip range(s). I don't know if this rule will work exactly for u, but it works for me in custom-rules using arno-iptables-firewall for blocking access to whole ip ranges which \begin edit\ equales domain names /edit end/, and also does NOT gripe about it. 

yes just change 127.0.0.1 to whatever ip and add a slash and then the netmask range and restart the firewall.

Example to block the WHOLE 224.0.0.0 range - IGMP/BROADCAST range, the following rule should suffice..

iptables -A OUTPUT -p all --destination 224.0.0.0/3 -j DROP
```

---

### Post by teresaejunior on 2010-01-22
The IP you get from the netstat command, and to use that (taken from "man iptables"):

```
Address can be either a network name, a hostname, a
network IP address (with /mask), or a plain IP address. Hostnames will be
resolved once only, before the rule is submitted to the  kernel.   Please
note  that specifying any name to be resolved with a remote query such as
DNS is a really bad idea.  The mask can be either a  network  mask  or  a
plain  number,  specifying the number of 1's at the left side of the net&#8208;
work mask.  Thus, a mask of 24 is equivalent  to  255.255.255.0.   A  "!"
argument  before  the  address  specification  inverts  the  sense of the
address. The flag --src is an alias for this option.  Multiple  addresses
can  be  specified,  but  this will expand to multiple rules (when adding
with -A), or will cause multiple rules to be deleted (with -D).
```

---

### Post by doas777 on 2010-01-22
i'm quite comfortable with the cli, but in this instance, it just does not fit my usecase. do you know of any gui applets?

---

### Post by jmszr on 2010-01-22
Overcast32,

I'm not sure if this is what you have in mind, but have you considered DansGuardian? - [https://help.ubuntu.com/community/Servers/DansGuardian](https://help.ubuntu.com/community/Servers/DansGuardian). - [http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic](http://www.howtoforge.com/dansguardian-content-filtering-with-transparent-proxy-on-ubuntu-9.10-karmic) - [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008) - 
[http://www.pilpi.net/journal/item-985.php](http://www.pilpi.net/journal/item-985.php) are some of the links.

---

### Post by teresaejunior on 2010-01-22
> **doas777 said:**
> i'm quite comfortable with the cli, but in this instance, it just does not fit my usecase. do you know of any gui applets?

No, but you can block domains in your OpenDNS profile!

---

### Post by doas777 on 2010-01-22
> **teresaejunior said:**
> No, but you can block domains in your OpenDNS profile!

thats kewl. I've been meaning to look deeper at openDNS (I just use their servers for now).

I'm less interested in blocking domains (can do that just fine in gufw) than the op is, but I would really like a gui that shows a list of connections (with their state, ports, and listening/sending application) that I can click to block/unblock etc, and clear logs about what got bounced. any ideas?

---

### Post by Overcast32 on 2010-01-22
Ok, that's a lot to look into - well a bit. I have been looking at Smoothwall, I would prefer something that runs under Ubuntu - as I would like to be able to use this system for other stuff as well.

I'm not sure the Netstat will work 100% for what I'm looking for as I would also like to log stuff and not necessarily have to be watching it 24/7. 

I'm far from a 'control freak' but I guess once you give your kids a bit too much freedom and they abuse it.... hehe, well, now we gotta swing the other way. But at least she told on herself ;)

I think Ideally I want something that will Monitor Traffic, allow me to block domains as needed, and perhaps more - I'll spend sometime looking into these suggestions. 

I let her hang out on MySpace - but it went too far, so she's got some 'work' to do to get back to there, but I'm well aware a bazillion proxies exist and I want to be able to catch those ASAP and block as well. A 'wildcard' block for domain names might be useful too. It may end up that I use more than one package - Thanks for the above Firewall script too.

Being a gamer, I still need a Windows System around - I've tried Wine and in some cases it does superb, but newer games can be a hassle. Otherwise, I'm looking at moving to Linux for everything else. That way I can keep my 'gaming' PC just stripped to WinBlows and Drivers.

I was actually thinking about setting up a stripped down install of Windows with only drivers and VMWare/Sun Virtual Box - and only using the WinBlows Kernal for gaming - but since I happened upon a working spare mainboard, I put a buncha' extras in there, setup a second monitor and just loaded 9.10 last night - curious to see it :)  Hardy Heron was the last version I tried, but that hard disk ended up going bad and I haven't reinstalled as I didn't have anywhere to go with the data on my existing NTFS disks, heh

Oh - and I had used OpenDNS in the past and still got an account there, with routing everything through a single host, it will be a more viable option. It never seemed to work just right - all the time - when all the PC's went straight through the router, in spite of me using OpenDNS for the DHCP DNS. It might have had to do with me not getting that client side service going right - unsure. But with a single point, I may well make this Linux box a DNS server itself and setup DHCP to hand out it's IP for DNS.

---

### Post by teresaejunior on 2010-01-22
> **Overcast32 said:**
> Ok, that's a lot to look into - well a bit. I have been looking at Smoothwall, I would prefer something that runs under Ubuntu - as I would like to be able to use this system for other stuff as well.

I'm not sure the Netstat will work 100% for what I'm looking for as I would also like to log stuff and not necessarily have to be watching it 24/7. 

I'm far from a 'control freak' but I guess once you give your kids a bit too much freedom and they abuse it.... hehe, well, now we gotta swing the other way. But at least she told on herself ;)

I think Ideally I want something that will Monitor Traffic, allow me to block domains as needed, and perhaps more - I'll spend sometime looking into these suggestions. 

I let her hang out on MySpace - but it went too far, so she's got some 'work' to do to get back to there, but I'm well aware a bazillion proxies exist and I want to be able to catch those ASAP and block as well. A 'wildcard' block for domain names might be useful too. It may end up that I use more than one package - Thanks for the above Firewall script too.

Being a gamer, I still need a Windows System around - I've tried Wine and in some cases it does superb, but newer games can be a hassle. Otherwise, I'm looking at moving to Linux for everything else. That way I can keep my 'gaming' PC just stripped to WinBlows and Drivers.

I was actually thinking about setting up a stripped down install of Windows with only drivers and VMWare/Sun Virtual Box - and only using the WinBlows Kernal for gaming - but since I happened upon a working spare mainboard, I put a buncha' extras in there, setup a second monitor and just loaded 9.10 last night - curious to see it :)  Hardy Heron was the last version I tried, but that disk ended up going bad.

You can by now use a predefined filtering policy in the OpenDNS profile (like moderate...) and enable stats. I don't know exactly if it still what you need, but it's very easy and could help. At least they would be prevented from visiting sites OpenDNS already knows of.

Do you know of any application that does what you want under Windows? Then it will be much easier to google for "linux alternative to appname"

---

### Post by Overcast32 on 2010-01-22
> **teresaejunior said:**
> You can by now use a predefined filtering policy in the OpenDNS profile (like moderate...) and enable stats. I don't know exactly if it still what you need, but it's very easy and could help. At least they would be prevented from visiting sites OpenDNS already knows of.

Do you know of any application that does what you want under Windows? Then it will be much easier to google for "linux alternative to appname"

Not offhand.. :)

I think I'll just give a few of these a try, it's a new install - so at worse I can just re-load once I figure out which I want. 

Thanks a ton for the input.

---

