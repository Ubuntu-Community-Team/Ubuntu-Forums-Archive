---
title: "Folding@home not working"
date: 2010-11-17
forum: General Help
---

### Post by awc_ on 2010-11-17
Initially I had the segmentation fault that everyone else is mentioning, i fixed that problem, now I get the following:

[05:44:41] - Ask before connecting: Yes
[05:44:41] - User name: awc26 (Team 11314)
[05:44:41] - User ID: 7DAF917B157CA49C
[05:44:41] - Machine ID: 1
[05:44:41] 
[05:44:41] -configonly flag given, so exiting.
Terminated
root@andrew-desktop:~/folding# 


suggestions?
Thanks,
awc

---

### Post by awc_ on 2010-11-17
ok, so looking over it again with a less sleepy and more coherent mind, the above is not a problem at all >_>

The main problem is this:
[15:19:08] + Attempting to get work packet
[15:19:08] - Will indicate memory of 3960 MB
[15:19:08] - Connecting to assignment server
[15:19:08] Connecting to [http://assign.stanford.edu:8080/](http://assign.stanford.edu:8080/)
[15:19:08] - Couldn't send HTTP request to server
[15:19:08] + Could not connect to Assignment Server
[15:19:08] Connecting to [http://assign2.stanford.edu:80/](http://assign2.stanford.edu:80/)
[15:19:08] - Couldn't send HTTP request to server
[15:19:08] + Could not connect to Assignment Server 2
[15:19:08] + Couldn't get work instructions.
[15:19:08] - Attempt #6  to get work failed, and no other work to do.
Waiting before retry.

I think its a net problem on this end, so I'll see if the IT guys that do the net for my dorm can help out.

---

