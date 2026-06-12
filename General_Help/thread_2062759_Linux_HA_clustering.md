---
title: "Linux HA clustering"
date: 2012-09-25
forum: General Help
---

### Post by javanoob on 2012-09-25
Hi all,
 
I have a few high level questions with regards to this setup and i hope you gurus can enlightened me.
 
I have 2 nodes (A and B).
 
With Linux HA,
 
q1) Do i still need to sync data/applications between this 2 nodes or will it be sync automatically ?
 
e.g i got an app (myprog) running in background, if node A fail, node B  will takeover by starting the app (myprog) on node B itself, but myprog  must 1st exists in node B isn'it it ?
 
q2) I believe HA depends heavily on the heartbeat daemon, so therefore, if these related processes went down, won't my HA fail ?
 
where is these daemons installed ? on both node A and B ?
 
q3) I have read about certain apps would still need to be manually restarted or configured in a HA environment (warm standby)
 
I can't really picture out what kind of apps would require so in a HA environment ? (database?)
 
From what i see, if i have 2 sets of similar apps on both A and B, if A  goes down, the apps will be start on B and that's it. (why would it  still need any manual intervention ?)
 
Regards,
Noob

---

