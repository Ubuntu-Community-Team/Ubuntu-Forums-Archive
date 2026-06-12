---
title: "Repeating Segfaults after upgrade?"
date: 2009-07-07
forum: General Help
---

### Post by cuddles71 on 2009-07-07
Evening folks. Last night I logged into my (headless) broadcasting system and saw a message saying that a reboot was needed to complete an upgrade (running Jaunty). After rebooting, I keep getting this:

```
Jul  7 20:44:52 johnnyfever kernel: [90160.276029] sc_trans[24572]: segfault at f0 ip 0810db9c sp b2e92060 error 4 in sc_trans[8048000+2ad000]
Jul  7 21:02:10 johnnyfever kernel: [91197.244285] sc_trans[29128]: segfault at f0 ip 0810db9c sp b300f060 error 4 in sc_trans[8048000+2ad000]
Jul  7 21:11:06 johnnyfever kernel: [91733.458813] sc_trans[1209]: segfault at f0 ip 0810db9c sp b2f21060 error 4 in sc_trans[8048000+2ad000]
Jul  7 21:21:53 johnnyfever kernel: [92381.194053] sc_trans[3609]: segfault at f0 ip 0810db9c sp b2e68060 error 4 in sc_trans[8048000+2ad000]
Jul  7 21:28:30 johnnyfever kernel: [92777.702701] sc_trans[6127]: segfault at f0 ip 0810db9c sp b3033060 error 4 in sc_trans[8048000+2ad000]
Jul  7 21:34:24 johnnyfever kernel: [93131.124363] sc_trans[7789]: segfault at f0 ip 0810db9c sp b2f71060 error 4 in sc_trans[8048000+2ad000]
```

I've checked the Shoutcast forums, and they say it's only happening to users running Jaunty. So any ideas what's causing this, and how to fix it?

---

### Post by cuddles71 on 2009-07-08
Bump.

---

