---
title: "firefox isn't opening the ica link with the citrix receiver"
date: 2011-07-14
forum: General Help
---

### Post by deostroll on 2011-07-14
Hi,

I am using ubuntu lucid lynx. Recently I had downloaded the citrix receiver and configured my FF to co-work with this software. But one day FF decides to use the Java client to do the job. Whenever the java-based client loads, the session is not initiated properly. I am not looking to solve this problem. The actual problem was that the citrix receiver software was working fine, and then one day, it, for some unknown reason, stopped.

My FF version is 3.6.18

---

### Post by toddyfranz on 2011-08-01
Hi

> **deostroll said:**
> Hi,
The actual problem was that the citrix receiver software was working fine, and then one day, it, for some unknown reason, stopped.


Please paste the output from

ldd /usr/lib/ICAClient/wfcmgr

I think that you have a libary lost. :o

Regards,
Torsten

---

