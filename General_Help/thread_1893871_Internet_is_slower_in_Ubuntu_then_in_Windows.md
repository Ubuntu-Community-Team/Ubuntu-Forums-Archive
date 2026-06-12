---
title: "Internet is slower in Ubuntu then in Windows"
date: 2011-12-11
forum: General Help
---

### Post by Rastafa on 2011-12-11
I noticed that loading web pages takes longer in Ubuntu then it does in Windows. The same problem is present on three different notebooks, with three different variants of Ubuntu - Ubuntu 11.10, Lubuntu 11.10 and Mint 12. All of these notebooks dual boot Windows, I've checked on all three and page loading is noticeably faster in Windows (both XP and Windows 7).

I've done ping tests on pingtest.net, in Ubuntu ping is about 50 ms and jitter is about 18 ms (but sometimes less), in Windows ping is 20-25 ms and jitter less than 10 ms. The results are same on all three notebooks. 

I use chromium in Ubuntu and chrome in Windows, but the same problem is in Firefox.

I have cable connection (UPC) download 10 Mb/s, upload 1 Mb/s and Cisco EPC2425 wi-fi router. The computers are connected to internet over wi-fi, but the problem persists even if I use ethernet cable.

I haven't tried yet, if the problem exists when I connect to internet somewhere else.

---

### Post by Spyderkid on 2011-12-11
You can use Google chrome if you want on linux. Just visit the chrome website.

Also what internet adapter do you have?

---

### Post by killermist on 2011-12-11
There are a huge number of variables in that which could be causing issues.

1.) a firewall (just in having to inspect packets to know if they should be allowed or blocked) can slow things down.
2.) if using a software rendering video driver instead of hardware accelerated could have a slowing effect
3.) any phishing/trustworthyness checks done by the browser before displaying content could be slowing things down.
4.) using DHCP instead of having static IP addresses/routes configured could cause some trivial slowdowns
5.) if windows caches DNS hits but Ubuntu (correctly) double-checks DNS resolution on a regular basis, that would add some overhead periodically
6.) animation/fancification of window rendering can slow things down by using "unused" CPU time

The list goes on.  I just ran out of things off the top of my head that are possible contributors.

As Ubuntu continues to (sometimes misguidedly) push for "more user-friendly" configurations, sometimes efficiency is sacrificed for prettyness/familiarity/whatever, and in doing so, things can slow down.

If you want to try a probably more fair benchmark, try burning and booting KNOPPIX and then do some comparisons against windows.

---

### Post by Rastafa on 2011-12-11
Thanks for help. I think I've found what was causing the problem, for some reason my primary dns server was not working, so I changed it and now everything seems to be fine.

---

