---
title: "Unable to enumerate USB device on port 5"
date: 2011-05-07
forum: General Help
---

### Post by Chevy787 on 2011-05-07
I'm getting "hub 2-0:1.0: unable to enumerate USB device on port 5" in the recovery console. 
It all started when I screwed up my sudo privlages and went to the system recovery console for help. I began to get spammed with this message "hub 2-0:1.0: unable to enumerate USB device on port 5". It constantly spams me with the message so that I'm unable to use the console.
I tried
1) Unplugging all external devices
2) Ripping out my Broadcom Bcm411 network card
3) Ripping out the battery and leaving it unplugged for 10mins or so

Nothing has helped so far, any suggestions?
Also, the device in question is a HP PAVILION DV2500 laptop running Ubuntu 11.04

**:Used old recovery console.**

---

### Post by jaminthorns on 2011-05-09
I'm having the same problem on my HP Pavilion dv6t. I'm pretty sure the problem is with the newest Linux kernel because I just updated my kernel after doing a new install of Ubuntu 11.04 and the problem occurred. I have also tried out the latest Fedora 15 beta that has the same kernel and it too has the same problem. The only solution I see for now is to downgrade your kernel until a fix is released.

---

