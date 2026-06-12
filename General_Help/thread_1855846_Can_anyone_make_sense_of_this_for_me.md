---
title: "Can anyone make sense of this for me?"
date: 2011-10-07
forum: General Help
---

### Post by c3ntury on 2011-10-07
Foreword - I'm posting this here because after trying on various forums and such, I'm at my wits end and... this is my last hope of getting some intelligent answers from a forum I know in the past has been brilliant.

Anyway.

My mobile dongle is connected via an amplified USB cable to a 3G router, and occasionally, it'll just *die*. I have to restart the router to get it to work again, and the router still shows typical lights which would indicate that it's working, alas otherwise. 

I've peered into the logs and grabbed the relevant bit in which the connection dies. Could anyone help me make some sense of it please? 

```
ep 17 22:44:07 (none) local2.debug pppd[22946]: sent [LCP EchoReq id=0xc4 magic=0x67433435][size=2]
Sep 17 22:44:07 (none) local2.debug pppd[22946]: rcvd [LCP EchoRep id=0xc4 magic=0x7b21b57 67 43 34 35][/size]
Sep 17 22:44:46 (none) local2.notice pppd[22946]: Modem hangup
Sep 17 22:44:46 (none) local2.debug pppd[22946]: ipcp: down
Sep 17 22:44:46 (none) local2.info pppd[22946]: Connect time 1988.8 minutes.
Sep 17 22:44:46 (none) local2.info pppd[22946]: Sent 145721457 bytes, received 678530321 bytes.
Sep 17 22:44:46 (none) daemon.notice miniupnpd[23650]: received signal 15, good-bye
Sep 17 22:44:47 (none) local2.debug pppd[22946]: Script /etc/ppp/ip-down started (pid 27323)
Sep 17 22:44:47 (none) local2.debug pppd[22946]: CCP: Down event in state 1!
Sep 17 22:44:47 (none) local2.notice pppd[22946]: Connection terminated.
Sep 17 22:44:48 (none) local2.notice pppd[22946]: Connection terminated.
Sep 17 22:44:48 (none) local2.debug pppd[22946]: Script /etc/ppp/ip-down finished (pid 27323), status = 0x0
Sep 17 22:44:48 (none) local2.info pppd[22946]: Exit.
Sep 17 22:45:20 (none) local2.notice pppd[27443]: pppd 2.4.4 started by root, uid 0
Sep 17 22:45:20 (none) local2.err pppd[27443]: Failed to open /dev/ttyUSB0: No such device
Sep 17 22:45:20 (none) local2.info pppd[27443]: Exit. 
``` 

Any help would be appreciated! 

Thanks, c3ntury.

---

### Post by LowSky on 2011-10-07
What if you use a regular USB cable? Amplified cables are not all built the same, you can only extend only so far, and sometimes it leads to a bad connection if the cable isn't up to snuff.

If the same result happens from a standard 1 meter (~3 feet) cable. Then we can figure out of its a hardware or driver issue.

---

