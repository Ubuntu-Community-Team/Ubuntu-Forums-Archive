---
title: "using ifconfig to find ip of my dns server"
date: 2012-06-21
forum: General Help
---

### Post by johnmerlino on 2012-06-21
I run ifconfig to find the ip address of my dns and I see something like this:


	inet 192.168.2.2 netmask 0xffffff00 broadcast 192.168.2.255
	inet 172.16.227.1 netmask 0xffffff00 broadcast 172.16.227.255

what's the difference?

---

### Post by papibe on 2012-06-21
Hi johnmerlino.

'ifconfig' won't give you your DNS server.

If you are running dnsmasq, run this:
```
cat /var/run/nm-dns-dnsmasq.conf
```

If not (including previous versions) either of this will do:
```
cat /etc/resolv.conf

nslookup ubuntu.com

dig ubuntu.com
```
Regards.

---

### Post by johnmerlino on 2012-06-23
> **papibe said:**
> Hi johnmerlino.

'ifconfig' won't give you your DNS server.

If you are running dnsmasq, run this:
```
cat /var/run/nm-dns-dnsmasq.conf
```

If not (including previous versions) either of this will do:
```
cat /etc/resolv.conf

nslookup ubuntu.com

dig ubuntu.com
```
Regards.

So cat /etc/resolv.conf will give me my public facing ip address or the local address assigned from my LAN?
thanks for response

---

### Post by papibe on 2012-06-23
> **johnmerlino said:**
> So cat /etc/resolv.conf will give me my public facing ip address or the local address assigned from my LAN?
thanks for response

Neither of those.

The only addresses contain in /etc/resolv.conf are:
[LIST]
[*]The addresses of your nameservers if you are not running dnsmasq. For instance, this is what I have on my home server:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
My server is resolving names using OpenDNS.

This is another typical example:```
nameserver 192.168.1.254

``` In this case, my desktop is using my router as DNS, which is set through DHCP.


[*]If you are running dnsmasq (default on 12.04). The address contain in /etc/resolv.conf is loopback of your own machine:
```
nameserver 127.0.0.1
```
[/LIST]

Does that help?
Regards.

---

### Post by johnmerlino on 2012-06-23
> **papibe said:**
> Neither of those.

The only addresses contain in /etc/resolv.conf are:
[LIST]
[*]The addresses of your nameservers if you are not running dnsmasq. For instance, this is what I have on my home server:```
nameserver 208.67.222.222
nameserver 208.67.220.220
```
My server is resolving names using OpenDNS.

This is another typical example:```
nameserver 192.168.1.254

``` In this case, my desktop is using my router as DNS, which is set through DHCP.


[*]If you are running dnsmasq (default on 12.04). The address contain in /etc/resolv.conf is loopback of your own machine:
```
nameserver 127.0.0.1
```
[/LIST]

Does that help?
Regards.

Your right in that the lan ip address on my computer is not the same as the ip address in resolv.conf. Just the host id is different between the two. That seems a little confusing then. I have a belkin router attached to my motorola modem. I assume that it uses DHCP to dynamically set the local ip on my computer. But I still don't see why the local ip is different than the address in resolv.conf. How exactly is that address being generated in resolv.conf. And more importantly, when I run sudo apt-get install apache2 to install apache on my web server, what ip address is being used for the default of the site, the local one or the one located in that file?

thanks for response

---

### Post by HiImTye on 2012-06-23
if youre trying to find your internet facing IP address then use a tool such as [http://whatsmyip.org](http://whatsmyip.org)
for your network IP you can just use your network tools such as ifconfig

---

### Post by dcstar on 2012-06-23
> **johnmerlino said:**
> 
.........
But I still don't see why the local ip is different than the address in resolv.conf.
.........

You obviously do not understand what DNS and other networking items are, I suggest you do some research before trying to do anything that may end up breaking your system.

---

