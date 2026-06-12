---
title: "Internet Blocked"
date: 2010-11-05
forum: General Help
---

### Post by trilobyte- on 2010-11-05
Hi there.

Recently I've been very impressed with Ubuntu 10.10, so I decided to make the move back to it. There's been one small problem though. Every time I install Ubuntu on any machine here, a few sections of the internet don't work. Trying to load Firefox takes about 4 minutes, then with the "No page was found" error. Yet, going on Google Chrome and the internet works fine? Also the same with Emesene and Pidgin, Emesene doesn't seem to log in but Pidgin gets through.

Any help would be great, thanks.

---

### Post by The Cog on 2010-11-05
I wonder if you have a faulty DNS server there, that doesn't handle IPv6 queries properly. You could try disabling ipv6 in firefox and see if that helps:
* In the address bar, enter the address **about:config**
* search for ipv6
* set network.dns.disableIPv6 to true

---

### Post by trilobyte- on 2010-11-08
Hi there.

Sorry for the late reply. Funnily enough that night I did a firmware upgrade on my router, which for some odd reason seems to have fixed the issue without needing to do the about:config in Firefox.

Thanks. :)

---

