---
title: "How do I disable the ondemand cpu governor in 10.10.  9.10's tricks don't work."
date: 2010-10-12
forum: General Help
---

### Post by at165db on 2010-10-12
I'm an embedded linux developer, and using the ondemand cpu governor impacts my compile time noticably.  In Kubuntu 9.10, my code base takes ~4 minutes to compile with the governor set to performance, and ~6 minutes to compile with the governor set to ondemand.  This probaby has something to do with that our makery is recursive, so you cannot run it in parallel, and the difference between using 1 core at 1.2GHz vs 2.8GHz is a lot.

In the past, I fixed this problem by editing /etc/init.d/ondemand so that it always set the policy to performance.  That seemed to stop working at some point, so I started using KDE's System Settings->Power Management menu.  I could edit the profiles and under the CPU and System section, I could set the CPU governor policy.

That setting is gone now.  How can I force my desktop to stop using the ondemand cpu frequency setting.  The copany is paying the powerbill, and 1-2 minutes of my time per compile is worth more than the power savings :->.

---

### Post by zokara on 2010-10-18
Try removing the /etc/init.d/ondemand from all run levels:

$ update-rc.d -f ondemand remove

and reboot.

---

### Post by at165db on 2010-10-27
That worked.  Thanks!

---

