---
title: "Router Weirdness"
date: 2012-02-07
forum: General Help
---

### Post by gunksta on 2012-02-07
Systems Involved:
- Belkin N750 Wireless Router connected to DynDNS via a paid account.
- "Server" running Ubuntu 11.10 (It is a converted desktop, running headless.)
- Various laptops / desktops running 11.10 and 1 Android tablet running 2.3+Touchwiz.

I just installed a new router in my apartment and I'm having a very unexpected problem. I have an old desktop converted to a "server" that runs a small website for friends and family with a local static IP address. I have an account with DynDNS which is set up properly.

I am currently at work, and I can successfully browse to: [www.team-kandy.net]("http://www.team-kandy.net"). But, when I go home and use my local wireless connection, I can no longer see the site. I get a 404 error. I can browse to the server using its local IP address, but my remote ssh, and http connections are all dead. What gives? Other than my inability to see my own site, the Internet functions as expected. I can search Google, stream Amazon Instant Videos, etc. 

I am at a loss to explain why I lose access to my server, using its URL when I am sitting in the room next to it but it works fine when I am here at the office 20 miles away. I've confirmed this same behavior with my girlfriend's tablet. She can browse to the URL when using her 3G connection but she must use the local IP address when she uses the local wireless network. Attempts to bypass DNS also fail. If I look up my current IP address and try to browse directly to that site, it fails if I am using the wireless network but works via her tablet's 3G connection.

Thoughts?

---

### Post by efflandt on 2012-02-07
Most broadband routers (and Linux by firewalls by default) do not do loopback (LAN2LAN via public IP) to avoid possible IP spoofing.  That is the reason you cannot access your LAN server via your public IP from the same LAN, and your router forwarding only works from the internet side.

---

### Post by gunksta on 2012-02-08
Interesting. My old router did this just fine. Perhaps this is an improvement after-all. It is something of a pain though locally. Maybe time to experiment with a cloud server.

---

### Post by jamesisin on 2012-02-08
It is true you should not be able to access the inside from the outside through the inside (for example using ssh over your Internet facing IP address); however, you ought to be able to access your Web page in a browser.

Are you able to do that?

---

### Post by gunksta on 2012-02-08
> **jamesisin said:**
>  however, you ought to be able to access your Web page in a browser.

Are you able to do that?

Nope. The connection to the site is a regular http:// connection. It is not encrypted in any way but I can not access it when I am on my LAN. I can only access it when I am on another network. Yet, I am able to access all other content from within my LAN, so I know that basic DNS is working correctly.

And, I get the same behavior when I attempt to go directly to the external IP address. Thus proving the problem isn't DNS related, which is what I assumed was the problem initially (before I posted here). 

After I convinced myself that DNS was working fine and my port forwarding scheme was working as expected, I got a little confused.

---

### Post by gunksta on 2012-02-08
I should note that I've tried this with several desktops/laptops running 11.10, my phone and my girlfriend's tablet. All devices have the same response. The phone / tablet give the most interesting results, since they can not browse to the site when using the wireless LAN connection but everything works as expected when using their 3G connections.

---

### Post by jamesisin on 2012-02-08
Do you get a 404 if you try to access something specific like this:

[http://team-kandy.net/piwigo/upload/2012/02/06/pwg_high/20120206202751-dbfc99f8.jpg](http://team-kandy.net/piwigo/upload/2012/02/06/pwg_high/20120206202751-dbfc99f8.jpg)

---

### Post by gunksta on 2012-02-08
OK -- Looks like I misspoke slightly. Firefox tells me that it can not establish a connection. I know that over-all, things are working fine, because I am on my LAN as I write this and I can obviously access the Ubuntu Forums (and the rest of the Internet). 

I can positively ping my URL, but I can not establish a HTTP connection or a ssh connection to it.

---

### Post by afoin on 2012-02-08
You could use a Web Proxy.

---

### Post by gunksta on 2012-02-09
True, but then I have to set that up on all of the devices for which I want it to work. I may contact Belkin to see if there is some setting that I am just too blind to see.

---

### Post by CharlesA on 2012-02-09
> **gunksta said:**
> True, but then I have to set that up on all of the devices for which I want it to work. I may contact Belkin to see if there is some setting that I am just too blind to see.
I doubt there is a setting like that.

You'd need to use the local IP to connect locally, instead of the external IP.

---

### Post by jamesisin on 2012-02-10
For using ssh within your network you will use your internal IP address(es) as you really wouldn't want to enable your router to allow ssh to run out/in like that.  If I want to connect to one of my network machines from inside my network I use the appropriate 192 address; if I am outside I ssh to my external IP which is forwarded to one machine from which I can then internally connect to any machine inside-to-inside.

That being said, you should be able to get http working correctly without resorting to a proxy.

---

### Post by gunksta on 2012-02-10
I agree. I don't mind using the 192... address for ssh when I am on the LAN. I am the only person here using ssh and if someone else ever needs ssh access to the server, I can explain it to them. Anyone who know what ssh is can be counted on to remember a couple of addresses.

My problem is with the lack of http:// connectivity. That is annoying and I have to explain it to the girlfriend who isn't real interested in work-around. She prefers tech that just works.

---

### Post by Cheesemill on 2012-02-10
There are two options I can think of here:

1- Run an internal DNS server that returns the correct internal IP address to clients on the LAN. Tricky to set up but no configuration needed on the clients.

2- Add an entry to the hosts file on each of the clients. Easy to set up but you need to do this on all of the clients.

I run an internal DNS server on my home network for just this reason.

---

### Post by CharlesA on 2012-02-10
> **Cheesemill said:**
> There are two options I can think of here:

1- Run an internal DNS server that returns the correct internal IP address to clients on the LAN. Tricky to set up but no configuration needed on the clients.

2- Add an entry to the hosts file on each of the clients. Easy to set up but you need to do this on all of the clients.

I run an internal DNS server on my home network for just this reason.
An internal DNS server would work. I do the same, but in my case, I just use the IP since my server has a static IP set and 192.168.1.2 is easy to remember. ;)

I use DNSMASQ for my local DNS, and it's fairly easy to set up. I have it running on my dd-wrt router.

---

### Post by jamesisin on 2012-02-10
Have a look at dd-wrt and see if you can install it on your Belkin:

[http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)

Presumably if you are not using your server as a local DNS then your router ought to be performing that task.  It should also have DNS server information which it checks (presumably those of your ISP unless you prefer something different).

---

### Post by gunksta on 2012-02-14
After talking to Belkin, it looks like I'm out of luck on using this router to do what I want to do. I may decide to return it. The port forwarding capabilities are not useful to me if I can't access it easily within my own network.

I looked and dd-wrt does not support this router, so that avenue is closed as well, unless I get another router. Its too bad. It is otherwise a very nice piece of equipment.

---

### Post by Cheesemill on 2012-02-14
I've never seen a home router that does loopback, only professional firewalls that cost a lot of money.

I do have this set up on the firewall I administrate at work but that's a WatchGuard XTM 510 which will set you back around £1500.

As I posted earlier I think an internal DNS server is the way to go, either set up on a server on your LAN (you could use your Ubuntu server), or by running dnsmasq on a router running dd-wrt.

---

### Post by CharlesA on 2012-02-15
Still a +1 to running a local DNS server. That is easier than trying to find a router to throw dd-wrt on, if that is what you want to do.

---

### Post by gunksta on 2012-02-15
Alright, I'm game. I'll install a DNS server on my server and disable the DNS service on the router. I just did an ```
apt-cache search dns
``` and I can see there are (of course) lots of options to choose from. Any thoughts regarding which I should look at the hardest? Other than some simple web-serving, we use the network for a fair amount of Amazon Instant Videos and what not. Nothing exotic on the consumption side.

---

### Post by CharlesA on 2012-02-15
I use dnsmasq.

[https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq)

---

### Post by gunksta on 2012-02-27
I played around with dnsmasq but had a hard time getting everything to work nicely together. In the end, I decided to use my old router and chain the new router from the old router. The old router runs a domain 192.168.1.* while the new router runs a domain 192.168.2.*. I disabled the wireless on the old router and now I am able to set everything up to work the way I want it to. As an added bonus, I can now separate my server from the rest of the network.

The old router passes through requests to the server and the new router. Because the new router is also running its own firewall and most of the network connects to the new router wirelessly, I have a second firewall, that does not have any port forwards, protecting those devices.

Probably not the most efficient set up, but it works and as an added bonus, I can now use my web-server from within my lan (the network controlled by the new router) because the server sits outside it and is connected via the old router.

Ain't networking fun.

---

