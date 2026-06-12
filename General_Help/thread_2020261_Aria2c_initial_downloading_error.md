---
title: "Aria2c initial downloading error"
date: 2012-07-08
forum: General Help
---

### Post by vokevybez on 2012-07-08
Whenever I start to download ***any*** torrent, for instance using ```
aria2c --bt-max-peers=210 --max-overall-upload-limit=1000K --max-upload-limit=1024K --seed-ratio=0.0 --seed-time=0 --max-download-limit=1024K --max-overall-download-limit=1024K --torrent-file= f.torrent

``` However when it starts to download the file, it outputs```
 2012-07-08 08:02:42.371062 NOTICE - IPv4 DHT: listening to port 6979

2012-07-08 08:02:42.384528 NOTICE - IPv4 BitTorrent: listening to port 6884

2012-07-08 08:02:42.385068 ERROR - IPv6 BitTorrent: failed to bind port 6884
Exception: [SocketCore.cc:308] errorCode=1 Failed to bind a socket, cause: Name or service not known
``` and then it starts to download the torrent. Is there any way to solve this error?
_***NB:I am using Xubuntu 12.04.***_

---

### Post by Merrattic on 2012-07-08
This is just aria2c trying to use IPv6 and failing. You can probably turn IPv6 off in aria2c's settings to get rid of the error. But it is nothing to worry about.

---

### Post by vokevybez on 2012-07-08
> **Merrattic said:**
> This is just aria2c trying to use IPv6 and failing. You can probably turn IPv6 off in aria2c's settings to get rid of the error. But it is nothing to worry about. That´s good to know, thanks for the information

---

