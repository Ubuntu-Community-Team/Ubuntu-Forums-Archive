---
title: "Server not accessible by name"
date: 2012-05-17
forum: General Help
---

### Post by DOS286 on 2012-05-17
Here's the rub: My wireless router died. I replaced it with Netgear (model wndr3400). After switching out the router, I can no longer access my little home media server by name. I can still access it by IP address but not by the name. I thought it must be some setting on the router but I can't find it. The netgear folks have not been much help. They insist it's my ubuntu machines (both the host and client) and said "I don't know much about Linux, so good luck!"

I'm hoping one of the fabulous people in the Ubuntu community will be able to guide me into problem solving this. Any one have any ideas?

---

### Post by josephmills on 2012-05-17
> **DOS286 said:**
> Here's the rub: My wireless router died. I replaced it with Netgear (model wndr3400). After switching out the router, I can no longer access my little home media server by name. I can still access it by IP address but not by the name. I thought it must be some setting on the router but I can't find it. The netgear folks have not been much help. They insist it's my ubuntu machines (both the host and client) and said "I don't know much about Linux, so good luck!"

I'm hoping one of the fabulous people in the Ubuntu community will be able to guide me into problem solving this. Any one have any ideas?

what do you get when you type into the terminal ```
hostname -A
```
Is it different that what it use too be? 

Hope that this helps.

---

### Post by papibe on 2012-05-17
Hi DOS286.

My first guess is that your new router doesn't provide DNS for your LAN.

If both machines are Ubuntu machines, you can access each other using the 'zero config' style. For example:
```
ping servername.local
```
I hope that helps.
Regards.

---

### Post by DOS286 on 2012-05-18
> **josephmills said:**
> what do you get when you type into the terminal ```
hostname -A
```
Is it different that what it use too be? 

Hope that this helps.

It's the same but with ".local" at the end.

If I ping hostname.local, I get "Could not resolve hostname: Name of service not known"

It was my thought as well that the DNS function was either not there or not working. Is there a way around this?

---

### Post by goodvikings on 2012-05-18
edit your /etc/hosts file to insert the line:

<name of box> <ip address>

(it might be the other way around.)

Then, sudo /etc/init.d/networking restart

When names are resolved this file is checked. Here the name will resolve to an address and all will be good.

All this assuming you don't use a dynamic IP on that box....

---

### Post by DOS286 on 2012-05-18
@goodvikings: I assume I do this on the host machine? I can't get it to work. The lines already in the "hosts" file were the other way around so I followed that syntax. When I restarted networking it gave the notice: "Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces" It looked like it went ahead and reconfigured anyway.

I still cannot get a connection, either to the windows share or with ssh, to the host with the machine name, just with the IP address.

Do I need to tell the router to look for this domain name information some how?

I don't know if it's related, but I cannot browse the network with Nautilus either. When I double click on the workgroup, it grinds for a long time and then pops up with: "Error: Failed to mount Windows share
Please select another viewer and try again."

---

### Post by goodvikings on 2012-05-18
Hmmm if the hosts entry doesn't fix it (possibly restart the box?) then it's not a DNS issue I believe. Which means I'm out, sorry.

---

### Post by steeldriver on 2012-05-18
I remember having an issue like this with *one* of my machines at home

When I dug into it I *think* the problem was that it was running an older version of dhclient which didn't know how to expand the 

```
send host-name "<hostname>"
```

directive in /etc/dhcp/dhclient.conf

Newer versions will expand that so it always reflects what's in /etc/hostname - in older versions it was necessary to specify the hostname literally in dhclient.conf as well as in /etc/hostname

---

### Post by DOS286 on 2012-05-18
Hmmm... But why would it work with the old router and not with the new? 

How do I update dhclient? The machine is up-to-date with the automatic updates. Do I need to do something different for dhclient?

---

### Post by steeldriver on 2012-05-18
Well my current router is a WNDR3800 and I would be surprised if your 3400 did not support it 

Are you sure your computers are not configured to use external / public DNS server(s)? iirc you want the local hosts to use the router as DNS server (assuming it runs one), so that it can resolve *local* names (i.e. the ones it has sucked up via dhclient "send host-name" responses) and just pass locally-unresolved names up to whatever public DNS server you are using 

i.e. the router is both a DNS server - for the machines inside its LAN - and a DNS client - talking to a public server to resolve external names - you only give the public DNS server address to the router. 

That should happen automatically if you let DHCP take care of specifying the DNS server AND your hosts correctly "send host-name".

---

### Post by DOS286 on 2012-05-18
> **steeldriver said:**
> Well my current router is a WNDR3800 and I would be surprised if your 3400 did not support it

Me too. I was sure it would, and that swapping out routers would not be an issue. 

> **steeldriver said:**
> Are you sure your computers are not configured to use external / public DNS server(s)? iirc you want the local hosts to use the router as DNS server (assuming it runs one), so that it can resolve *local* names (i.e. the ones it has sucked up via dhclient "send host-name" responses) and just pass locally-unresolved names up to whatever public DNS server you are using 

No, i'm not sure. How do I check this? Why would the settings on the client computers change when the router was changed?

> **steeldriver said:**
> i.e. the router is both a DNS server - for the machines inside its LAN - and a DNS client - talking to a public server to resolve external names - you only give the public DNS server address to the router. 

That should happen automatically if you let DHCP take care of specifying the DNS server AND your hosts correctly "send host-name".

I agree. It should happen automatically. I generally assume that everything should happen automatically just like I want it to. I'm often disappointed. :( Can you tell me how to check that my clients are using the router as a DNS server instead of some public / external DNS server? I think this may be the problem. When I ping my server name, I get a response with an external IP address listed. Thanks for your help.

---

