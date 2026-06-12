---
title: "Sporadic Suspend Crashes"
date: 2012-02-13
forum: General Help
---

### Post by matthisd on 2012-02-13
Hey,

I have been trying to fix this for the past 2 months. I have tried various sleep functions, and they all cause this issue, but I want to fix it specifically when using Tuxonice.

I suspend, which seems to run smoothly. When I try to restart, somtimes it is fine, other times it freezes during loading. The only error I have been able to find is associated to:

uhci_hcd 0000:00:1a.0: host controller process error, something bad happened!

but resume seems to continue first, then stop immediately after this:

dbus[915]: [system] Failed to activate service 'org.freedesktop.Avahi': timed out

I have tried both the PAE and regular versions, both cause this issue.
Any help would be appreciated, even pointing me in the right direction... I have searched online quite a bit!

lg
Matthis

---

