---
title: "Firewall Settings For Outgoing uPnP Access"
date: 2012-03-05
forum: General Help
---

### Post by Mad-Halfling on 2012-03-05
Hi, I've got a MythTV box I've set up as a backend server, I've also put MediaTomb on it and these are working fine and serving up files on my Android tablet.  However, trying to access the uPnP resources from XBMC on my Ubuntu laptop results in the access timing out.  If I disable the firewall on my laptop, it works fine.  My outgoing permissions are set to permissive, so it doesn't seem to be blocking anything going out.  XBMC works fine with the MythBox plugin, connecting to the same MythTV backend, it's just the uPnP access that doesn't seem to work.  I've now allowed incoming access for all connections from the IP of the MythTV box and this seems to solve the problem, but obviously this isn't as ideal as only opening up the appropriate ports from it, but I can't work out which ones these should be.  I don't get any connection refusal messages in my firewall error log, which is also a bit odd, as I was expecting these to show me which ports were being refused (I'm guessing that there must be some sort of connect-back occurring from the server when I connect to its uPnP resources).

As this happens on both MythTV and MediaTomb I'm assuming that it's a uPnP issue - any ideas on how I can diagnose/fix this properly, please?

---

