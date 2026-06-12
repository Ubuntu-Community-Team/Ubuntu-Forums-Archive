---
title: "firefox loading pages slowly"
date: 2010-08-14
forum: General Help
---

### Post by estanton on 2010-08-14
So this is an odd problem and I hope someone can help me out. I just switched my internet connection from cable to DSL and I've noticed that when using Firefox webpages load extremely slowly. This is only occuring in Ubuntu, not when I run Win7 on the same machine. Also it doesn't occur when using Chrome. It seems the same thing is happening within Thunderbird as well. Any ideas on what is causing this? Thanks!

---

### Post by Blackbird_13 on 2010-08-14
Same here with Firefox 3.6.8.

Just done a fresh install of lucid on my dad's pc. It takes 15 seconds to load every page:

- not using wireless
- download speed of 1 mb/sec when I did a system upgrade, so connection generally is ok.
- version 3.6.8 in jaunty on same pc is fine, not so lucid. 
- 3.6.8 is also fine in windows xp on same pc.

Disabling ipv6 had no effect.

Firefox 3.6.8 is also slower on my pc compared to jaunty - can take 1 -3 seconds to load page.

Any ideas would be welcome. For the first time in years I am thinking of dumping Firefox.

---

### Post by [Shawn] on 2010-08-14
i've had the same issue. But it was when I had Ubuntu 9.10. It was a  ipv6 issue. There is also the settings around it
change these
1.) network.http.pipelining > Make it True
2.) network.http.pipelining.maxrequests > Make it 8 or 10
3.) network.http.proxy.pipelining > Make it True
4.) network.dns.disableIPv6 > Make it True
After this restart should work fine then

---

### Post by estanton on 2010-08-14
Definitely an issue with ipv6, turning it off did the trick.

---

