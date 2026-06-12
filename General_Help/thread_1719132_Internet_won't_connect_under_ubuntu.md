---
title: "Internet won't connect under ubuntu"
date: 2011-04-01
forum: General Help
---

### Post by TruePurple on 2011-04-01
My internet stopped working except for a few pages I often use (and those were working spotty) I thought it was my ISP service. I called support, they tried to solve the problem, then I waited a few hours for them to try something else, then they did something else again the next day. 

The internet under ubuntu firefox is still not working, but I decided to boot up my old crappy XP machine to check its internet, internet is working fine on it.

So something got messed up on ubuntu, I tried clearing browser cache, but that didn't work. I restarted the PC several times, no success.

Ubuntu 10.10 64bit

---

### Post by TruePurple on 2011-04-02
Turns out I needed to "true" network.dns.disableIPv6 to get my browser.

Are there some negative effects to having IPv6 disabled?

One person had me comment out a nameserver in the list with a #, could that have some negative effects?

---

