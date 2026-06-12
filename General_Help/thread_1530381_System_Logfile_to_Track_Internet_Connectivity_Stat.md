---
title: "System Logfile to Track Internet Connectivity Status?"
date: 2010-07-13
forum: General Help
---

### Post by tknight55 on 2010-07-13
Do any of the current logfiles (10.04) track the status of Internet connectivity, or can a logfile be created to do that? I am having intermittent broadband modem disconnect issues and I would like a way to check and see if the signal has dropped while I am away from the system. Thanks for any assistance.

---

### Post by TechBeastie on 2010-07-13
I think most network-related events are sent to the standard kernel log (/var/log/kern.log and/or /var/log/messages), and I imagine you could set up a simple script to monitor that log for such events.

---

