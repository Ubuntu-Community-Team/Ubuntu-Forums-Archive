---
title: "Do I need Some Security? What?"
date: 2011-11-10
forum: General Help
---

### Post by JoshuaMiller0 on 2011-11-10
Hi,

I have recently been thinking about the security of my Linux and was wondering if it was worth it.

I have not got wine, anything running off my Internet [SIZE=1](IF THAT MAKES ANY SENSE) and I do not do anything inter-computer, inter-OS etc. (I run mostly locally)

So my question is; Do I need any security? If so - what sort of security????
[/SIZE]

---

### Post by Rodney9 on 2011-11-10
You are fairly safe if you are behind a router, you can check it's effectiveness at [https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

It's also worthwhile to read this [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Rodney

---

### Post by Dangertux on 2011-11-10
> **JoshuaMiller0 said:**
> Hi,

I have recently been thinking about the security of my Linux and was wondering if it was worth it.

I have not got wine, anything running off my Internet [SIZE=1](IF THAT MAKES ANY SENSE) and I do not do anything inter-computer, inter-OS etc. (I run mostly locally)

So my question is; Do I need any security? If so - what sort of security????
[/SIZE]

In my opinion read the stickies in the security section of the forum. As far as whether you need additional security measures in place that is up to you.

What do you have to lose? What threats are you exposed to regularly? A lot of users will tell you , no Ubuntu is fine out of the box. In some cases that may be accurate in others maybe not. Ubuntu / Linux are not  invincible, nothing is. The router argument while amusing hasn't been true in over a decade, the no open ports argument is pretty much the same. 

Thankfully if you read the security stickies you will find there is a lot that you can do to strengthen Ubuntu in terms of its default security. If you're new to Linux or security concepts in general and were only going to do a few easy things for casual desktop usage I would do these three. Use strong passwords, Configure your firewall, install NoScript in your browser.

That's just me, some say I'm paranoid. However, I consider myself realistic.

P.S : ShieldsUP was great at doing two things, selling Zone Alarm subscriptions and giving people a false sense of security.

---

### Post by haqking on 2011-11-10
> **Dangertux said:**
> In my opinion read the stickies in the security section of the forum. As far as whether you need additional security measures in place that is up to you.

What do you have to lose? What threats are you exposed to regularly? A lot of users will tell you , no Ubuntu is fine out of the box. In some cases that may be accurate in others maybe not. Ubuntu / Linux are not  invincible, nothing is. The router argument while amusing hasn't been true in over a decade, the no open ports argument is pretty much the same. 

Thankfully if you read the security stickies you will find there is a lot that you can do to strengthen Ubuntu in terms of its default security. If you're new to Linux or security concepts in general and were only going to do a few easy things for casual desktop usage I would do these three. Use strong passwords, Configure your firewall, install NoScript in your browser.

That's just me, some say I'm paranoid. However, I consider myself realistic.

P.S : ShieldsUP was great at doing two things, selling Zone Alarm subscriptions and giving people a false sense of security.

+1

DT no link to the security for newbies thread ? ;-)

[http://ubuntuforums.org/showthread.php?t=1873643](http://ubuntuforums.org/showthread.php?t=1873643)

and the under construction WIKI born from it [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by proxx1850 on 2011-11-10
Oke well , compared to a windows box.. you are fairly safe.
Well face it, a lot of attacks are done by p0wning the browser.
I recommend using "no script" and yes thats not really funny, nearly every website uses javascript and browsing with noscript active will ruin nearly everything.
It's more secure though.

A couple other things that will improve your security somewhat:

1)Set a static DNS server in your netw settings!
 
2)Set all your ip adresses to static.

3)Block all incoming traffic with iptables.

4)Change your default router password!(most ppl dont, really do that!)

5)Scan yourself with nessus.

6)Scan yourself with nmap and disable services that you dont use.

7)Block all icmp traffic including timestamping.

8 )Use a decent password! most ppl are stupid.

9)If you use ssh; use key pairs.

10)Dont be an idiot :)


Hope this helps.
I probably forgot a lot.

---

### Post by Dangertux on 2011-11-10
Static IPs do nothing for your security. I am fairly certain if an attacker is clever enough to break into your network they are clever enough to set a static ip. 

Also blocking ALL ICMP traffic is a great way to slow your network connection to a crawl.

---

### Post by proxx1850 on 2011-11-10
Sure , have you ever heard of fake DHCP servers?
I'm not claiming this to be the ultimate solution, but it helps.

About the ICMP you might be right, I never noticed speed reduction.

---

### Post by Dangertux on 2011-11-10
Yes I have heard of fake dhcp servers. Though this is a misnomer since they are in fact really dhcp servers. You can do all sorts of cool things with them including injecting payloads over tftp. However that tool you heralded in you former post. Nmap is commonly used by attackers to determine the layout of a network, fake dhcp servers and all.

---

### Post by proxx1850 on 2011-11-10
Oke :)
I think we are on the same line here.
What actually ment, is that with all static adresses one eliminates the need and use of DHCP server in general, which is a good pratice imo, as well for the tiny speed enhancement.
Ive been wrong before though :)

---

