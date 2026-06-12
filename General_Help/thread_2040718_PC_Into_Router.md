---
title: "PC Into Router?"
date: 2012-08-11
forum: General Help
---

### Post by ..jeff.. on 2012-08-11
Hi,

My PC is on 24x7 anyway, so I'm not too concerned about power. I have a router that is probably slowing my internet down, I can't install DD-WRT on, and is getting old (still kicking!). Alternatively, I have an idle PC that I can use. Is there any way I can turn the old PC into a router? Can I get the functionality that DD-WRT has? 

Finally, what hardware do I need to do that? I'm sure I'll need a new network card with at least 1 CAT5 in and 1 CAT5 out I'd like to have a few other wired (CAT5) connections (ie: I use a wired to connect my XBOX to my current router).


Thanks!

---

### Post by CharlesA on 2012-08-11
Why do you think your router is slowing down your internet?

If you want to use a PC as a router, you will need two network cards and running ip forwarding and NAT on that machine.

It can get a bit complicated if you are a newbie:
[https://help.ubuntu.com/community/Router/](https://help.ubuntu.com/community/Router/)

EDIT: An alternative is buying a cheap router that supports DD-WRT. I picked up a Dlink DIR-615 the other day for just that reason. It was about 40 bucks.

---

### Post by ..jeff.. on 2012-08-11
> **CharlesA said:**
> Why do you think your router is slowing down your internet?

Not gigabit and with it being so old, I'm not sure which versions of 802.11 it supports, but I'm positive its not anything within the last 6-8 years. my basis is: if I look for a new router today, and it doesn't have gigabit and/or 802.11g/n, would I buy it? no....

That does seem complicated, I know this is subjective but is it too complicated? I'll use the PC for more than a router, its just that if I can save $40-60 by doing this instead of a new router, that would be nice.

---

### Post by CharlesA on 2012-08-11
> **..jeff.. said:**
> Not gigabit and with it being so old, I'm not sure which versions of 802.11 it supports, but I'm positive its not anything within the last 6-8 years. my basis is: if I look for a new router today, and it doesn't have gigabit and/or 802.11g/n, would I buy it? no....

Gigabit really doesn't matter for anything other than internal network speed. An internet connection is nowhere near as fast as 1Gbps. The fastest I have seen is a bit over 100/100, but those are quite expensive.

The router I have now supports 10/100 and Wireless-n. I don't need gigabit on the router itself because I've been running an 8 port gigabit switch for a long, long time. Saves money on routers. ;)

If you don't need super fast transfer speeds on your internal network, just stick with a 10/100 router.

> That does seem complicated, I know this is subjective but is it too complicated? I'll use the PC for more than a router, its just that if I can save $40-60 by doing this instead of a new router, that would be nice.

It looks complicated to me and I've set one up like that before. I would not recommend it. I would totally recommend pfSense tho:
[http://www.pfsense.org/](http://www.pfsense.org/)

---

### Post by Bachstelze on 2012-08-11
The wiki page makes it looks more complicated than it really is. Basically, all you need is to bring up your second network inteface and add a bunch of iptables rules. (If you want added props like DHCP and DNS forwarding, install dnsmasq.) You really don't need to mess with the horror that is NetworkManager. I prefer this guide, which I find much less verbose

[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

but since it's for Gentoo you need to adapt it to Ubuntu (in particular, you can skip the first section about kernel configuration.)

---

### Post by CharlesA on 2012-08-11
> **Bachstelze said:**
> The wiki page makes it looks more complicated than it really is. Basically, all you need is to bring up your second network inteface and add a bunch of iptables rules. (If you want added props like DHCP and DNS forwarding, install dnsmasq.) You really don't need to mess with the horror that is NetworkManager. I prefer this guide, which I find much less verbose

[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)

but since it's for Gentoo you need to adapt it to Ubuntu (in particular, you can skip the first section about kernel configuration.)

+1. The last time I did it, I used iptables itself and didn't touch NetworkManager.

---

### Post by ..jeff.. on 2012-08-11
> **CharlesA said:**
> 
If you don't need super fast transfer speeds on your internal network, just stick with a 10/100 router.


I don't, but I would like super fast external speeds. Does that mean gigabit won't have a major impact on a router I get - or does your gigabit switch cover that and I still would need gigabit? Applying that to my PC / router, that seems to mean I would need to make sure I get a LAN card that supports gigabit.


> **Bachstelze said:**
>  You really don't  need to mess with the horror that is NetworkManager. I prefer this  guide, which I find much less verbose

[http://www.gentoo.org/doc/en/home-router-howto.xml](http://www.gentoo.org/doc/en/home-router-howto.xml)



Thank you! that is the type of guide I need. I prefer to use iptables / something easily customizable too. My goal would be to have 1 PC / router / nas / firewall instead of 4 different devices.

---

### Post by CharlesA on 2012-08-11
> **..jeff.. said:**
> I don't, but I would like super fast external speeds. Does that mean gigabit won't have a major impact on a router I get - or does your gigabit switch cover that and I still would need gigabit? Applying that to my PC / router, that seems to mean I would need to make sure I get a LAN card that supports gigabit.

If you want super faster internet you will have to pay for it, upgrading your router won't do a thing to affect your internet speed.

You can check what your current internet speed is here:
[http://www.speedtest.net/](http://www.speedtest.net/)

---

