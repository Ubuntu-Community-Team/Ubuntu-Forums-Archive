---
title: "Internet issues after clean install"
date: 2010-01-31
forum: General Help
---

### Post by jiggling_john on 2010-01-31
Right...

I had 9.04 working fine, no problems at all. Did a clean install of 9.10 and internet performance was dire - pages not loading or taking minutes to resolve the address. At first I thought it was a dns issue - I've already assigned them statically in my router. But this isn't the case, my windows machines and iphone can navigate to all pages through the same connection whereas ubuntu just sits there.

So... I did some digging, ipv6 was already turned off by default in firefox, so i disabled it completely by blacklisting ipv6 in etc/modprobe.d/blacklist.conf. A 'ip a | grep inet6' reveals nothing.

This didn't improve matters, then I found a random post in one of the bug trackers suggesting setting the MTU value to 1400 bytes in network manager.... This, I thought, had completely fixed the problem - pages now loaded without problem.

I'm now left with a weird remaining problem, pages that require login. After I type in a user name and password, the first login attempt always seems to hang - I have to click log in several times before it will work. This is especially a problem when trying to log into internet banking as obviously you'll get locked out if you keep trying to refresh! Again, these pages all load first time on non linux boxes...

So, er, any suggestions?

---

