---
title: "Running ifconfig &lt;interface&gt; down"
date: 2010-01-04
forum: General Help
---

### Post by enchance on 2010-01-04
I was running some tests on my network card and ran
```
ifconfig wlan0 down
```
and noticed that once the interface has been put down, the wireless disconnects as expected. Then suddenly after a few seconds it is suddenly automatically put up again and I get connected to the wireless again.

Is this really the way it's supposed to happen?

---

### Post by pbrane on 2010-01-04
Are you running Network-Manager too? The wireless connection will be handled by NM and re-establish if NM sees a signal.

---

### Post by enchance on 2010-01-04
> **pbrane said:**
> Are you running Network-Manager too? The wireless connection will be handled by NM and re-establish if NM sees a signal.

I see. I guess I was under the impression that when you put an interface down it stays down forever. So it connects when it sees a signal. That basically cleared it for me. Thanks pbrane!

---

