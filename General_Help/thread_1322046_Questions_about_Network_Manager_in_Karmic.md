---
title: "Questions about Network Manager in Karmic"
date: 2009-11-10
forum: General Help
---

### Post by Louigi Verona on 2009-11-10
Hello guys!

I have a couple of questions.

1. Quite a number of people when upgraded to Karmic had a serious bug with "Insufficient privileges" when editing connections and having a timeout on DSL.
However, although the amount of people with this problem seemed to be large when looking at bug announcements in launchpad, I haven't heard this bug mentioned much anywhere. Does it mean that on a larger scale not so many people have been really affected?

2. Does anyone know why did the bug occur? I thought it was a software problem. But since obviously not everybody have had this problem, what is the reason? Hardware? Modem model? ISP type?

3. Several solutions have been proposed, including installing a daily build from launchpad. I did this and it worked after I created a connection and did not check "available to all users". However, this did not seem to work for everybody (and I still haven't rebooted, so who knows if it will work for me fully). Anyway, even if it is a solution, will this fix ever appear in Updates or will users have to go read forums and install a specific version from daily builds? If it will appear in updates - when? Isn't it a blocker kind of bug?

---

### Post by Giblet5 on 2009-11-10
I always install wicd, which removes network-manager.

It just works, has a better icon, an interface that is usable, more features, and a smaller footprint.

---

### Post by Louigi Verona on 2009-11-10
However, it does not do DSL. And I do not have wireless internet at home, only DSL. I had to use pppoeconf for many days which is not very convenient.

---

### Post by Giblet5 on 2009-11-10
> **Louigi Verona said:**
> However, it does not do DSL. And I do not have wireless internet at home, only DSL. I had to use pppoeconf for many days which is not very convenient.

Oh My! Won't I be disappointed since I have DSL too. :lolflag:

And four active gigE NICs on this workstation, routing traffic between 4 subnets. I guess your setup is too complicated for me! ;)

Wicd works for my demanding architecture just fine, and I really don't see what DSL would have to do with anything: it's just another transport.

---

### Post by Louigi Verona on 2009-11-10
Can you please explain? I would love to get hints on this, but when I installed wicd, it only showed Wireless. I saw no way to enter a username and password to start a DSL connection. I have no routers or whatever, just ADSL modem.

ps: yeah, and I later read on forums that wicd cannot help with DSL.

---

### Post by Giblet5 on 2009-11-10
> **Louigi Verona said:**
> Can you please explain? I would love to get hints on this, but when I installed wicd, it only showed Wireless. I saw no way to enter a username and password to start a DSL connection. I have no routers or whatever, just ADSL modem.

Do you mean the ADSL modem is in your PC?

Mine's on the desk here. There is no authentication involved (that would be silly since ADSL isn't exactly a hackable architecture). On = connected. Off = disconnected.

One advantage that I probably have...

If you have an external box, then you definitely want to get a [Linksys router]("http://www.buy.com/retail/product.asp?sku=209036921&listingid=51516376"). Yeah, it's pricey, but you will thank me.


Seriously, a Linksys DSL router is a must-have. I have two spares under my desk.

Wireless is a plus, but [Linksys sells 10/100Mbps ethernet switching DSL routers]("http://www.amazon.com/Linksys-EtherFast-Router-4-Port-BEFSR41/dp/B00004SB92") too. Cheap.

You configure the router via a web interface and it saves your configuration in NVRAM. They provide DHCP and firewall service too.

---

### Post by Louigi Verona on 2009-11-10
I have an external box and no router. Now I understand that a router is a good thing to have, but I am afraid we went off-topic. Fixing a problem by buying hardware is not my ideal of an operating system upgrade.

Thanks for sharing your experience though.

---

### Post by Giblet5 on 2009-11-10
> **Louigi Verona said:**
> I have an external box and no router. Now I understand that a router is a good thing to have, but I am afraid we went off-topic. Fixing a problem by buying hardware is not my ideal of an operating system upgrade.

Thanks for sharing your experience though.


Sorry for the sidetrack, but I think it was informative.

Your ADSL modem is, by any measure, an unusually featureless one. Sorry, but it's true. I hope the service is really cheap.

Even without a router, I don't have to do anything to have internet access. This modem provides DHCP without the router. Plug the ethernet cable from the PC to the modem, select "Automatic Config" and within five seconds, you're rolling.

I did find [this how-to on making the modem work with wicd]("http://kubuntuforums.net/forums/index.php?topic=3104329.0"), if you can't get a better answer on network-manager.

---

### Post by Louigi Verona on 2009-11-11
Great geek stuff.

I have to explain the reason behind my questions.
1. I am curious.
2. I want to suggest Karmic to my friends, but until network is fixed, I am afraid I cannot do it. They are not tech people and uninstalling the app which is there by default and installing the new one WITHOUT the Internet is not a great experience. I personally worked in 9.04 before that and had no problems. Having upgraded to 9.10 I had a difficult time - no Internet in GNU/Linux means you cannot access frums to read advice and you cannot install anything too. I have a dual boot so I had to login to Windows to read up what's wrong.

I do hope someone can answer those questions.

---

### Post by habana on 2009-11-11
I use an ADSL modem, upgraded to Karmic and found that Network Manager worked perfectly - unlike Jaunty where NM continually reset itself to a default setup which was useless to me. I spent hours trying to resolve it without success. 

If that worked OK for me on an upgrade I would be fairly confident that a clean install would work OK for your friends so go ahead, what have they got to lose?

---

### Post by Giblet5 on 2009-11-11
> **Louigi Verona said:**
> Great geek stuff.

I have to explain the reason behind my questions.
1. I am curious.
2. I want to suggest Karmic to my friends, but until network is fixed, I am afraid I cannot do it. They are not tech people and uninstalling the app which is there by default and installing the new one WITHOUT the Internet is not a great experience. I personally worked in 9.04 before that and had no problems. Having upgraded to 9.10 I had a difficult time - no Internet in GNU/Linux means you cannot access frums to read advice and you cannot install anything too. I have a dual boot so I had to login to Windows to read up what's wrong.

I do hope someone can answer those questions.


You're correct to wonder why that doesn't work, but it is also important to understand that your DSL config is an exception - not a rule.

Did you file a bug report on network-manager yet?

It sounds to me like it's warranted, and that is how you get this issue in front of the developer. He doesn't read these forums.

---

### Post by Louigi Verona on 2009-11-11
There are many bug reports on launchpad concerning the issue. And they did (at least partially) solve it. My question is - when will it be delivered to the end user?

My DSL setup is typical for Moscow home Internet - a modem and DSL. Most people here use such a setup. I have had no problems with it neither with 8.10 nor with 9.04 and no problems in any of the Windows ever.

---

