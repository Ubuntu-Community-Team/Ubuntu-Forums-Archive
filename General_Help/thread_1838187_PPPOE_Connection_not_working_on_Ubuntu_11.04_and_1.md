---
title: "PPPOE Connection not working on Ubuntu 11.04 and 11.10"
date: 2011-09-03
forum: General Help
---

### Post by chirag64 on 2011-09-03
Ohk, so I've been using Ubuntu since a couple of years now.

A few months back, I had updated my Ubuntu to 11.04 (and probably made a few software updates after that) and that's when my internet connection simply stopped working. I tried to fix the problem by deleting my settings and what not, but it just did not work :(

So I thought the problem must be somewhere inside my system beyond my powers and hence I stopped trying to fix it.

When Ubuntu 11.10 Beta1 came out a couple of days ago, I downloaded the iso image and booted from the live CD, but even then it did not work, giving me the same error that it did in 11.04

```
Sorry, I scanned 1 interface, but the Access Concentrator of your provider did not respond.
Please check your network and modem cables. Another reason for the scan failure may also
be another running pope process which controls the modem
```So I tried booting off from an old Ubuntu 9.04 Live CD, and guess what, the connection started immediately without an error. 

I'm not sure if its the new version of pppoeconf in the new Ubuntu or something else that is causing this problem. I'm completely helpless in this case. Any help would be appreciated :confused:

**Edit:** OK, I tried the 11.10 disc on my friend's computer and it worked fine on his computer which has the same ISP connection as mine. So clearly the fault is in my PC...does the 11.10 Live CD use settings of an existing installation of Ubuntu?

---

### Post by Wampyra on 2011-10-16
Bumping into the wall here too...

Is there any way to fix this?

Thanks

---

### Post by Wampyra on 2011-10-16
P.S. I tried
```
sudo pppoeconf
```

After setting it up 
```
ifconfig pppoe
```
gave resoult
```
pppoe: error fetching interface information: Device not found
```

---

### Post by chirag64 on 2011-10-28
Yep, even I got same result as Wampyra
Anyone knows how to fix this? :(

---

