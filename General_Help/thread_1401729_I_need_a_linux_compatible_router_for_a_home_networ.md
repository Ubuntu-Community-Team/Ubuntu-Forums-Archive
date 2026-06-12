---
title: "I need a linux compatible router for a home network"
date: 2010-02-08
forum: General Help
---

### Post by 3pinner on 2010-02-08
I need suggestions on a linux compatible wireless router 
that allows VPN access.
Right now I have a linksys wired router that is pure hell to set up for VPN, and no matter what I do, it just won't allow me to connect with my server at work unless I disconnect the router and plug directly into my broadband modem.


Any suggestions?
Thanks!

---

### Post by oshunluvr on 2010-02-08
I'm not sure what you mean by linux compatible but Linksys WRT54G routers are linux based can be flashed with several different types of firmware. I have used one called HyperWRT in the past and now use Tomato.

[http://en.wikipedia.org/wiki/Linksys_WRT54G_series](http://en.wikipedia.org/wiki/Linksys_WRT54G_series)

Here's a search that will show you what versions are flash-able or not

[http://www.dd-wrt.com/site/support/router-database](http://www.dd-wrt.com/site/support/router-database)

You can pick up used models on ebay for $30 or so...

---

### Post by switch10 on 2010-02-08
The WRT54GL is awesome.  It uses open source, Linux based firmware.  I just bought one.

---

### Post by pirateghost on 2010-02-08
A VPN is designed in such a way that you should be able to tunnel through, regardless of router.  there should be no ports to open or specific traffic to allow.  what router do you currently have?

personally i prefer to build my own router/firewall, and utilize a switch to carry the traffic to other machines.

if you have a spare machine lying around the house, grab an extra nic and check out pfsense or vyatta

---

### Post by 3pinner on 2010-02-08
> **pirateghost said:**
> A VPN is designed in such a way that you should be able to tunnel through, regardless of router.  there should be no ports to open or specific traffic to allow.  what router do you currently have?

personally i prefer to build my own router/firewall, and utilize a switch to carry the traffic to other machines.

if you have a spare machine lying around the house, grab an extra nic and check out pfsense or vyatta

Yes that is what they are supposed to do, but they don't.
I have never been able to get this router to pass VPN through. Tried all settings, ready to try different router.

---

### Post by warp99 on 2010-02-08
What model do you have? You can flash it with DD-WRT or Tomato firmware which may give you the features you need or at least make it much easier to set up. 

[http://dd-wrt.com/site/index](http://dd-wrt.com/site/index)

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

I personally use DD-WRT on a Linksys WRT54G2, the "melted frisbee", and hands down it's 100% better then the stock firmware. Can SSH and VPN without any issues whatsoever.

---

### Post by 3pinner on 2010-02-08
> **warp99 said:**
> What model do you have? You can flash it with DD-WRT or Tomato firmware which may give you the features you need or at least make it much easier to set up. 

[http://dd-wrt.com/site/index](http://dd-wrt.com/site/index)

[http://www.polarcloud.com/tomato](http://www.polarcloud.com/tomato)

I personally use DD-WRT on a Linksys WRT54G2, the "melted frisbee", and hands down it's 100% better then the stock firmware. Can SSH and VPN without any issues whatsoever.

Its an older model BEFSR41.
I don't know if that firmware will help, but I plan on purchasing a wireless one anyway. maybe I'll try it and see if it works. If it messes up the router, itll be trash anyway.
Thanks for the tip.

---

### Post by t4thfavor on 2010-02-08
+1 to WRT54GL make sure it's an L.

Have you ever thought about which subnet your router is on. One of the most common problem with VPN's is both sides of the tunnel are on the same subnet. 

Make sure your router is giving addresses on a different network than the work network, or it will not work regardless of router.

i.e
yournet=192.168.50.0/24
worknet=192.168.51.0/24

instead of
yournet=192.168.50.0/24
worknet=192.168.50.0/24

---

### Post by Joe Ker1086 on 2010-02-08
I use the wrt54gl version 5 flashed with ddwrt and have no problems with vpn for work. Didnt even need to set anything up in the router for the vpn to be honest....use cisco vpn but my vpn on a windows vista box....I have never known a router to be the problem for vpn not working. if you can access the internet and your vpn is set up right you shouldnt have any problems with vpn...

---

### Post by Oatworm on 2010-02-08
I've seen this behavior with Linksys routers before myself, but that's only when I was dealing with Microsoft PPTP dial-in VPNs since they use GRE 47, which most Linksys routers I've run across don't seem to support.  I have a Netgear at home that I can dial in through without a problem, though, for whatever that might be worth.  

I'll also point out that, if you're trying to dial in via a Linux client to a Microsoft PPTP VPN and the AD domain on the other end uses a .local suffix, you're going to have some DNS issues since .local is reserved by your local Linux machine.  Fortunately, there's a workaround documented [here]("https://help.ubuntu.com/9.10/serverguide/C/likewise-open.html") (scroll down to the Troubleshooting section, especially the nsswitch.conf configuration example).

---

### Post by warp99 on 2010-02-08
> **3pinner said:**
> Its an older model BEFSR41.
I don't know if that firmware will help, but I plan on purchasing a wireless one anyway. maybe I'll try it and see if it works. If it messes up the router, itll be trash anyway.
Thanks for the tip.

That model is not supported under DD-WRT. Newegg.com is always running specials on routers that are DD-WRT compatible, they even note which ones can use DD-WRT. I picked up my router on special re-manufactured for $25 including shipping:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124364&cm_re=linksys_wireless_router-_-33-124-364-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124364&cm_re=linksys_wireless_router-_-33-124-364-_-Product)

If you want to spend a little more than I would suggest getting the original WRT54GL since it has dual external antennas for better reception:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190&cm_re=linksys_wireless_router-_-33-124-190-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16833124190&cm_re=linksys_wireless_router-_-33-124-190-_-Product)

---

### Post by 3pinner on 2010-02-09
thank you all for the suggestions. I will purchase that router.
I suspect it is the issue t4thfavor noted above, I have not checked which subnets are being used either at my end or at the office, I only know if I connect directly to the DSL modem, it can get through fine.

My work computer runs Windows XP, so I am indeed using Microsoft PPTP. Seems from what I have read that most if not all Linksys routers have trouble supporting this.
It'll give me something to play around with while it snows.

I'll post back with further questions I'm sure.

Thanks!

---

### Post by t4thfavor on 2010-02-11
Hope it worked out for you, I just was thinking you may have to forward port 47 into the pptp server itself as some routers cannot make the gre connection. 

Update the firmware on your current router, and see if that helps. 

Check back with us, I am curious to find out if the subnet was part of the problem.

---

