---
title: "logging network activity"
date: 2010-11-03
forum: General Help
---

### Post by hwttdz on 2010-11-03
I'd like to essentially log the firefox status bar "waiting for x...", "transferring from x...", all those messages.  Really what I'm after is a log of all servers contacted.  Any ideas on how to go about this?

---

### Post by hwttdz on 2010-11-03
A sort of roundabout way is to turn on dnsmasq and do local dns cacheing with query logging.  And I've set the log to ~/dnsmasq.log as well as making that world readable (since I'm the only one with access to the cpu anyways).  And I'll just be doing this long enough to find all the adservers that are hanging slowing my browsing and to add them to my hosts file.

---

