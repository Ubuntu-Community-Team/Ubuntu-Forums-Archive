---
title: "Why is loading so very slow when accessing web sites?"
date: 2011-04-27
forum: General Help
---

### Post by zzmel on 2011-04-27
Hi:

I have just installed ubuntu 10.1 along side my windows xp.  It installed nicely and boots up promptly.  When I try to go to a web site, it takes forever to load. :confused: It can take up to 1 minute to load a page.  Why is that.  I thought that Linux was supposed to be faster.  When I go back to windows, I don't have this problem.  Can anyone advise me what to do?  Thanks very much for your support.  :)

Mel

---

### Post by 3rdalbum on 2011-04-27
Your ISP or router might not support IPv6, which Ubuntu supports by default and which everything will have to use in a couple of years when we run out of IPv4 addresses.

Ubuntu usually tries to communicate with websites via IPv6, and if there's no reply it tries the same using IPv4. This can sometimes lead to a delay depending on what, exactly, is not compliant with IPv6.

Go to the Network Manager applet, go to Edit Connections and make sure that your preferred connection has IPv6 set to "ignored". Save your changes and, to be sure, reboot.

If IPv6 is already set to "disabled", then you might be in a wifi signal black-spot; depending on the quality of the wireless driver in Linux the problem might be more pronounced in Linux than in Windows. I'm assuming you're using wifi?

---

### Post by SkyNet2029 on 2011-04-27
You could just have a bad DNS nameserver.
I know that when in window I don't have this problem, but linux defaults to the router 
(192.168.xx.xx) as its primary nameserver. To fix this:

Network Manager applet> Edit Connections> select your connection>set ipv4 to automatic(DHCP Addresses only) and put in a decent nameserver.

I use google DNS for this...

in network manager>ipv4>DNS Servers:  8.8.8.8,8.8.4.4
notice the comma to separate Primary from Secondary DNS.

Select Available to all users (bottom left) and hit Apply.
Your network will go offline at this point. Just left click the icon in tray and select your network interface. It will reconnect using proper DNS names.

Hope that helped.

---

