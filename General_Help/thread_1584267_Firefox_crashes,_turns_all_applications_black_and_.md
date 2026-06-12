---
title: "Firefox crashes, turns all applications black and white"
date: 2010-09-28
forum: General Help
---

### Post by kazza765 on 2010-09-28
Hi all,

Firefox crashing isn't a problem, it's not something that happens very often. However when it does crash, it turns all the other programs I'm running permanently black-and-white (same color as if they were not responding). Any new programs I launch also start in black-and-white, including if I restart firefox. The only way I've found to fix this is to log out and back in. This is frustrating, since I'm often running things that take hours or days to complete.

The most recent time it occurred instead of turning everything black and white, they just went black. I've attached a screenshot of what I'm talking about. This only happens with firefox. Other programs that crash can be killed normally and everything else keeps running fine.

[IMG]http://imgur.com/siREOl.jpg[/IMG]

I'm running 10.04, and firefox 3.6.10 on an iMac 27". Any help would be much appreciated.

---

### Post by P4man on 2010-09-29
Not going to be easy to troubleshoot if you cant reliably reproduce it :S

My first suspicion would be the theme you are using. Which one is it?

Next up, compiz. You seem to be using it; if it happens again, try disabling desktop effects without restarting X. Just open a terminal or press alt+F2 and type:

```
metacity --replace
```

If that solves the blackness, then its a compiz plugin or possibly videodriver related.

---

### Post by kazza765 on 2010-09-30
Thanks. It seems to be related to compiz. Rebooting compiz fixes the issue so at least I have a workaround now. I'll have to try messing with my settings to see if I can correct it.

First up, need to find a webpage that consistently crashes firefox so I can test things :).

---

