---
title: "Third party firmware for routers (Tomato, DD-WRT etc)"
date: 2009-07-16
forum: General Help
---

### Post by Andy06 on 2009-07-16
Anyone have experience in loading Tomato, DD-WRT or similar open source linux based firmware onto Linksys routers?

1.Was it worth it? Better functionality? Better usability? Significantly better than Linksys' own firmware?

2.As long as I use Linksys, do I have to be ultra careful with compatibility?

3.Any other firmware apart from Tomato and DD-WRT that is worth considering?

4.Am going to be buying a new router/gateway, what brand do people recommend? (Linksys, Netgear, Buffalo, D-Link, Belkin etc etc)

Thanks a lot

---

### Post by t4thfavor on 2009-07-16
I have been using Tomato, OpenWRT, and DD-WRT for the last 7 years, and I must say I'm not sure how I got along without it.

I primarily use Tomato if I only need enhanced (basic) functionality. I use DD-WRT if I need some suffering (sorry), and OpenWRT when I want some advanced wacky setup that I can't get with Tomato (like a bridge, or a VPN server etc.)

I have only really used Linksys WRT54G(S)(L) so I'm not sure about the other brands. I do know that some buffalo routers come with more flash, and more RAM for running more services, but I'm not sure which ones.

The Tomato firmware is great, and has awesome support for QoS, Port Forwards, and UPNP NAT-PMP. I love how its easy to use, and has regular support releases (not scheduled, but often enough)

If there i anything else you would like to know, I have been around the custom Linksys firmwares since 2002, and know a fair bit about them.

---

### Post by lovinglinux on 2009-07-16
> **t4thfavor said:**
> I have been using Tomato, OpenWRT, and DD-WRT for the last 7 years, and I must say I'm not sure how I got along without it.

I primarily use Tomato if I only need enhanced (basic) functionality. I use DD-WRT if I need some suffering (sorry), and OpenWRT when I want some advanced wacky setup that I can't get with Tomato (like a bridge, or a VPN server etc.)

I have only really used Linksys WRT54G(S)(L) so I'm not sure about the other brands. I do know that some buffalo routers come with more flash, and more RAM for running more services, but I'm not sure which ones.

The Tomato firmware is great, and has awesome support for QoS, Port Forwards, and UPNP NAT-PMP. I love how its easy to use, and has regular support releases (not scheduled, but often enough)

If there i anything else you would like to know, I have been around the custom Linksys firmwares since 2002, and know a fair bit about them.

Is it safe to use them? Have you ever damaged a router?

---

### Post by JMarley1117 on 2009-07-16
I had been using DD-WRT on a linksys WRT54G for a year or so pretty much just for the signal boosting option(xmit power) and for me that was reason alone to make the switch. I recently had to buy a new router so I picked up the WRT54GL and decided to switch to tomato. It took some getting used to because the DD-WRT had a GUI that was very similar to the default linksys firmware but the tomato GUI was easy to adjust to plus it has some features that make things super simple like static network ip with dhcp. 

So as far as which one to use its personal preference depending on what you need it to do, but bottom line it is a beneficial upgrade to a great router.

---

### Post by RealG187 on 2009-07-16
I have an [NSLU2]("http://bestwikiever.wikidot.com/NSLU2"). It's not a router but is a Linksys product running open firmware.

Like to get on [XLink Kai]("http://bestwikiever.wikidot.com/Kai") with Xbox you need either:

* A PC running the software
* A Linkys router with 3rd party firmware

My NSLU can run the software. Since routers are basically computers when I say a PC running the software I guess a router or NSLU count because they are tiny computere (See the link above)

---

### Post by hibliss on 2009-07-16
I have used Sveasoft Talisman, DD-WRT (Mini, Micro,Standard, and Mega), and Tomato. 

My favorite personally is Sveasoft. It can do most of the same things, however VPN setup is very easy, which is the main reason I switched to aftermarket firmware in the first place.

---

### Post by Andy06 on 2009-07-16
> I use DD-WRT if I need some suffering (sorry)

Really? Its bad? What did you dislike in particular?

Everyone, 

Pls also drop your router brand recommendations, I know some people have a VERY STRONG leaning towards some brands and I'd love to get a consensus.

Also,
While all these third party firmware may be great, are they really that much better than the stock firmware that linksys ships? I ask because all of the functions that I need or the open source firmwares offer, all seem to be built right into the linksys firmware and they update whenever needed.
Perhaps few years ago Linksys firmware wasn't that great and all these third party solutions popped up and now they have improved?

Thanks a lot

---

### Post by slickflick on 2009-07-16
so whats the benefit of using this new firmware?

---

### Post by t4thfavor on 2009-07-16
I will NOT advocate sveasoft due to the bad karma they have earned within the comunity, just google it. (I started out with them)

I had lots of trouble with earlier DD-WRT (like V < V21). The routers would lock up, and act improper. Sometimes I would lose my dhcp server, sometimes DNS, sometimes both. I stopped using them for a few years, as it started to become a more commercial product, and less of an OSS endeavor. 

The ethernet bridge feature of DD worked great though, and it is the reason I still use the firmware now and then.


You get all kinds of benefits with third party firmware xmit power, antenna control, true commandline access, ssh management, snmp, better wireless encryption, more firewall rules, layer 7 QoS, Regular QoS, Bandwidth monitoring, system logging via syslogd, multiple ddns clients, and the list is much longer than this. You have to start using it, and you will soon understand whats up.


I have only ever had a problem one time while flashing the router, it was easily cleared up by using the linksys utility to tftp a stock formware image back and then reflashing through the gui again. The key is when going from Linksys firmware to third party that you pick the correct image for your model router (WRT54GS use the WRT54GS.bin and WRT54Gv4 use WRT54Gv4, etc). After you convert, you can pretty much use any compatible image. 

It's really a whole new world of control.

Think of it as taking a 40USD home router and turning it into a 500USD small office router, (in terms of software reliability, though I have never had a hardware failure either).

Please, try it yourself, and I promise you that you'll like what you find.

---

### Post by RealG187 on 2009-07-16
> **slickflick said:**
> so whats the benefit of using this new firmware?Extra features that the stock firmware will not do

---

### Post by hibliss on 2009-07-16
> **t4thfavor said:**
> I will NOT advocate sveasoft due to the bad karma they have earned within the comunity, just google it. (I started out with them)


I knew about this, but I still like their product.

At this point, the newest DD-WRT is on par, before it was not.

I have a Linksys WRT54GS v2 at home running Sveasoft, and a few Linksys WRT54G routers in the office running DD-WRT. Be VERY careful with the versioning on the new Linksys routers. After Cisco bought them, they started making a lot less capable product.

The WRT54GL is a decent router still, but if I was to buy a new Router I would get the **_[Asus WL500g Premium]("http://usa.asus.com/products.aspx?modelmenu=1&model=1121&l1=12&l2=43&l3=0")_**. It has much more flash ram than most models, and even without aftermarket firmware it can have an HDD attached for use as network attached storage (NAS).

With DD-WRT Mega, it is a beast of a router, acting as a NAS and VPN box in my other office.

Can the factory Linksys firmware handle VPN connections internally now? I am not talking about VPN passthrough, I mean a VPN connection to the router.

---

### Post by Andy06 on 2009-07-16
What about the new WRT310N and WRT610N routers? Are they compatible with OSS firmware? 
The latest Linksys router firmware seems pretty good, offers almost everything I need, but I would still try Tomato if it was better.

What about brand recommendations? Everyone using Linksys? Anyone on Linksys, Netgear, Buffalo, D-Link, Belkin?

---

### Post by t4thfavor on 2009-07-16
I use Linksys because of the price point, its about half as expensive as the ASUS wl500G premium (with alot less features)

Recently I have been using MR3201A routers for custom AP only installs, they ave atheros radios in them, and are 100mw (higher power) out of the box. They also tend to have 8mb flash, and 32MB ram for extra applications.

Other than those, I have not used another brand that I can recommend.

---

### Post by Agent ME on 2009-07-16
I've been considering putting DD-WRT micro on my WRT54G (it's a v6, with barely any flash space). Sometimes my router has problems with the connection or with UPnP, so I figure doing this might help it a bit.

---

### Post by GoldenSun on 2009-07-16
I have used a airlink ar430w with dd-wrt for about 7 months now.  Couldn't be happier as it is a traveling router.  I just set it up for whatever my needs happen to be at the time.  Such as wireless repeaters, bridges, router, switch, whatever you need it to be.  

I haven't used the other 2 firmwares, so my opinion is biased towards dd-wrt.

---

### Post by RealG187 on 2009-07-16
[http://www.sveasoftsucks.com/](http://www.sveasoftsucks.com/)

[http://wrt54g.thermoman.de/#readingpleasure](http://wrt54g.thermoman.de/#readingpleasure)

Who is James?

Is Sveasoft is company that made the firmware on Linksys Routers?

---

### Post by t4thfavor on 2009-07-17
Hes the guy that owns the company who "maintains" the software. I also think he works in the FUD department with them.

---

### Post by RealG187 on 2009-07-17
What do you mean FUD Department?

---

### Post by t4thfavor on 2009-07-17
Fear Uncertainty, and Deception. Its the tactics he used to try to bufffalo people into helping him violate the GPL.

---

### Post by hibliss on 2009-07-18
FUD is Fear Uncertainty and Doubt

---

### Post by Andy06 on 2009-07-19
So can I load these on the WRT310N and WRT610N? 
The compatibility lists for these firmwares seems pretty small (I guess limited to the hardware that has been tried and tested under a whole range of conditions). I would be just doing it for the sake of it though. I've never quite had a need that the Linksys firmware could not fulfil but then again I would never discover something better if I din't try.

---

### Post by hibliss on 2009-07-19
For those routers, my advice would be DD-WRT. You can check whether they are supported, with what firmware revision, and the flash procedure for each model here - [http://dd-wrt.com/dd-wrtv3/dd-wrt/hardware.html]("http://dd-wrt.com/dd-wrtv3/dd-wrt/hardware.html")

---

### Post by t4thfavor on 2009-07-20
> **hibliss said:**
> FUD is Fear Uncertainty and Doubt

My bad, I knew that, I just mis spoke...

---

### Post by hibliss on 2009-07-20
You seem to know more than me about everything, so I was taking the one opportunity to correct you :D

---

### Post by t4thfavor on 2009-07-20
Bah, don't say that, now I have to quote that in my new SIG!!

---

### Post by thatsdaniel on 2009-07-24
I for one use, [http://www.gargoyle-router.com](http://www.gargoyle-router.com)
Ive used dd-wrt in the past, but since this has a opensource'd gui, I choose gargoyle.
There are other gui's around for openwrt as well, if you need more options.

---

### Post by t4thfavor on 2009-07-24
Stock images of openwrt now come with a really god gui. Only problem is it takes up alot of flash for other apps.

---

