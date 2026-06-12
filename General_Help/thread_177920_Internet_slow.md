---
title: "Internet slow"
date: 2006-05-17
forum: General Help
---

### Post by namit on 2006-05-17
Hey all

I have dual boot on my computer but for some reason Windows response on firefox is just that little bit faster

Anyone have this problem?

Anyone know how to fix it?

---

### Post by frodon on 2006-05-17
The linux firefox version is endeed slower than the windows one, you should try swiftfox it's a firefox version optimized for AMD peoscessors :
[http://ubuntuforums.org/showthread.php?t=142798](http://ubuntuforums.org/showthread.php?t=142798)
There are optimised versions for intel proscessors too i think

---

### Post by DougC on 2006-05-17
I get an issue where Linux will set my DNS servers slightly wrongly.

in /etc/resolv.conf I get the first entry as my router and the second as my ISP's secondery DNS server, this results in a slight delay before the web sites address gets resolved.

I have to stop DHCP from updating /etc/resolv.conf and set both entries to my ISP's DNS servers.

I'm not saying this is your problem, but have a quick check of /etc/resolv.conf to see.

---

### Post by namit on 2006-05-17
[QUOTE=frodon]The linux firefox version is endeed slower than the windows one, you should try swiftfox it's a firefox version optimized for AMD peoscessors :
[http://ubuntuforums.org/showthread.php?t=142798](http://ubuntuforums.org/showthread.php?t=142798)
There are optimised versions for intel proscessors too i think[/QUOTE]


I have an intel Centreno

---

### Post by frodon on 2006-05-17
See this page to find the optimized version which fit your prosc and then follow the guide to install it : [http://getswiftfox.com/releases.htm](http://getswiftfox.com/releases.htm)

---

### Post by namit on 2006-05-17
Hey no joy with that its still really slow, tried the swiffox and it runs faster but internet is still very slow.

Getting in the tab a loading... loading

---

### Post by Slim Odds on 2006-05-17
[QUOTE=DougC]I get an issue where Linux will set my DNS servers slightly wrongly.

in /etc/resolv.conf I get the first entry as my router and the second as my ISP's secondery DNS server, this results in a slight delay before the web sites address gets resolved.

I have to stop DHCP from updating /etc/resolv.conf and set both entries to my ISP's DNS servers.

I'm not saying this is your problem, but have a quick check of /etc/resolv.conf to see.[/QUOTE]

There is generally nothing wrong with your router being specified as a DNS server. Most NAT gateway/firewall routers also provide a DNS server (which is really just a DNS forwarding service, which may or may not cache DNS lookup results). If the router provides DNS caching, it may actually make things a bit faster. Especially if you have multiple machines that sometimes access the same places.

One easy way to test this is to make your router the only DNS resolver and then ping some sites by name.

I have one computer with a hard coded address on my home network. I specify the router as both the gateway address and the DNS server address and it works just fine (using a Netgear WGR614).

---

### Post by namit on 2006-05-18
I have a 3 com unit and it works perfect wiht the connection of windows.
Have an intel centreno wireless card 2200gb and it seams to be connecting up fine but just very slow.
I have pluged cable in and still same problem.

---

### Post by namit on 2006-05-19
It was a problem with the DNS just had to set it seperate in the routers config

---

