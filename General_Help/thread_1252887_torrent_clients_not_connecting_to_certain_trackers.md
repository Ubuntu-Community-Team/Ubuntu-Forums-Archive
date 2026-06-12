---
title: "torrent clients not connecting to certain trackers"
date: 2009-08-29
forum: General Help
---

### Post by nice_like_rice on 2009-08-29
Hi,

I have tried a couple of torrent clients but they all show the same problem - they will connect to certain trackers, but not to others. I have no idea why this could be, surely I have everything configured correctly seeing as some trackers work? Only around 30% of the trackers seem to work for me, it's not just a one-off tracker not working, I have tried many.

Ktorrent returns "Could not connect to host... unknown error". 

Am I just stupid and have got something wrongly configured, and certain trackers block eg. wrongly configured port forwarding? I know some of them block certain clients, but I checked that.


Also a side note - the trackers which *don't* work also don't respond to ping, the ones which do do. They do respond to tracepath, so they must be up. It may just be a coincidence? Or could it be that for example my ISP is blocking those trackers ( as this would block ping but not tracepath because its over UDP I think ).

Any help or suggestions would be greatly appreciated. 

david

---

### Post by lovinglinux on 2009-08-29
Most likely that the trackers are down or do not exist anymore. 

Also check if you have firewall rules that could be blocking outgoing connections on the tracker port. Some trackers use port 80, which will certainly be open, but others use ports like 6969.

---

