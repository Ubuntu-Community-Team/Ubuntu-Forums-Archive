---
title: "network problems"
date: 2009-10-07
forum: General Help
---

### Post by Big_Croc7 on 2009-10-07
Right, I've tried everything I can think of and I'm completely baffled. I don't consider myself that new to linux or ubuntu but this has got me. I have considerable but intermittent network problems. The problem is that network connections sometimes take a very long time, or frequently, fail completely. This happens with web browsing, mail downloads and ssh connections - web pages fail to load, and mail and ssh session get dropped, usually within 5 minutes (though sometimes they can last a long time and be fine). I'm running a wireless wpa-encrypted connection on kubuntu 9.04. It's not a hardware issue - the same pc runs ubuntu 7.10 absolutely fine, with no network problems at all. So what's different between the two that could be causing this? I suspected ipv6, but I don't think that's the issue - I've turned off ipv6 usage in firefox and it doesn't solve the problem. I've tried konqueror, firefox and opera and they all seem the same. I'm stuck, please help!
In cases it helps, modprobe -l gives the relevant wireless drivers as kernel/drivers/net/wireless/zd1211rw/zd1211rw.ko
and
kernel/drivers/net/wireless/zd1201.ko
but I think these are the same ones as are loaded on ubuntu 7.10, which hasn't got the problem.

---

### Post by Big_Croc7 on 2009-10-07
[deleted - problem not fixed]

---

### Post by dearingj on 2009-10-07
Have you tried using a wired connection, and if so do you get the same problem?

When the problem does happen, can you still ping your wireless router or any other system(s) on your network?

---

### Post by Big_Croc7 on 2009-10-09
I don't have physical access to the router, so I can't try a cable. Pings do still work ok. In fact, other connections to the same server can work ok still - I can have the same website open in two browser tabs, click on the same link, and one copy will load and one won't. Or I can be browsing ok, and it will drop an ssh session, or vice versa.

I've tried using alternative dns servers, but that didn't make a difference.

---

### Post by Big_Croc7 on 2009-10-17
Turning off ipv6 system-wide has helped enormously, but hasn't fixed it.  Which has made me even more confused why it's happening :-s

---

### Post by dearingj on 2009-10-17
Very strange. Perhaps you should try using a different DNS server. [OpenDNS]("https://www.opendns.com/") has reliable servers, and their site provides instructions on how to set your network/computers to use them.

---

### Post by Big_Croc7 on 2009-10-21
That's helped (changing the DNS - thanks), but the problem's not fixed. Web browsing mostly works now, but mail connections (imap) are almost always dropped still. Don't know if it's relevant, but pings return lots of duplicates (about 3-5 returns for every outgoing ping). This happens whether I ping the router or anything outside my local network, but not other pcs on my network. Unfortunately I can't change the router, but that's not the only thing, as 7.10 still runs fine. :confused:

---

### Post by Big_Croc7 on 2009-11-07
can anyone help me?

---

