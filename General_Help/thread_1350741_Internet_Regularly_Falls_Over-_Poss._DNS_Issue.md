---
title: "Internet Regularly Falls Over- Poss. DNS Issue?"
date: 2009-12-09
forum: General Help
---

### Post by Noit on 2009-12-09
Hi all, hope someone will be able to help me with this one because it's got me a bit stumped.

Basically, my internet connection falls over randomly. And not the whole internet connection- just web browsing. I can be chatting to someone on skype and someone else on pidgin with a torrent downloading in the background and then at the same time firefox is bringing up loading error pages.

Things I know it's not include the browser (Chromium's nightly build falls over in the same way), the router (as this was replaced only last week as it was doing stupid things, and I'd hoped that replacing it would resolve this issue as well), and the amount of bandwidth being used (as it still falls over when it's just the web browser running).

The biggest hint I've got to what's causing it is that I've tried running a ping in the background to various websites (the BBC, google, and my own company site) and at the point that the web falls over, the ping seems to pause (completes one ping, and then doesn't start a new one for as long as thirty seconds to a minute), without showing packet loss or a high ping time. Also, while I'm always pinging a domain name, the sudden lack of web browsing seems to be accompanied by the ping program swapping to showing the target's IP address only- which makes me think the issue is DNS related. But I've tried using alternate domain name servers, and it doesn't seem to have improved things.

In short- HELP! This is an amazingly irritating issue and not being able to fix it is bugging me even more.

---

### Post by StuartN on 2009-12-09
> **Noit said:**
> which makes me think the issue is DNS related. But I've tried using alternate domain name servers, and it doesn't seem to have improved things.

It is a long shot, but why not - any chance you are a BT Ireland subscriber? They are transferring their DNS servers over to Vodaphone right now and it is causing exactly this kind of behaviour.

Even if not, to test an alternative DNS server you can use the brand new Google Public DNS at 8.8.8.8 and 8.8.8.4 or you can use Open Dns 208.67.222.222 and 208.67.220.220. Put these numbers in your Network Manager configuration.

(the old BT Ireland servers were 192.111.39.1 and 192.111.39.4, replaced by Vodaphone 89.19.64.164 and 89.19.64.36 - which are also erratic).

---

### Post by Noit on 2009-12-09
I'm afraid not, O2 UK and I've been having this issue for what must be a month at this point. I've just been running namebench to find what the best replacement nameservers are, just going to pop those in and see how it goes.

---

### Post by rvndrk3233 on 2009-12-09
If its connection, NO. If you are still connected, try 4.2.2.2 on manual setup, anyway, it works for me with 9.10. 9.04 can use auto.

It has something to do with your router as well if you are behind one.You might have to force reboot the router. I know for a fact that 9.10 has DHCP issues with Wifi over WPA.

4.2.2.2 is a global DNs server available to internic networks.I doesn't belong to anyone.

setting up a better firewall helps, as sometimes the router itself is hacked remotely and your settings get scrambled if you dont add a custom firewall script. happens a lot with my linksys. I had to put dd-wrt on it and update it recently because of this.

MAKE SURE FIRMWARE (whatever you run) IS UP TO DATE. Hackers like out of date firmware.

Im on cable and unfortunatly hacks happen all the time in form of DDOS flood and DNS redirection.
DNS timeouts occur no matter what ISP I'm with and they make the connection crawl.

Check your signal strength if on WWAN devices like an aircard.Im not seeing my strength myself, but there is an option for it.

I know my signal comes and goes an WWAN.Its just the area, Im surrounded by brick.

---

### Post by JCoster on 2009-12-09
For what it's worth I'm with O2-UK in Durham and I have exactly the same issue on both Ubuntu and MS machines.

I'm trying OpenDNS but for some reason my connection only uses it sometimes?

Let me know how you get on, but I think it's a major screw up on O2's end- I've had nothing but trouble with them since I moved from BT broadband in July.

JC

---

