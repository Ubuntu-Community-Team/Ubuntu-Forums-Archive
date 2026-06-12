---
title: "nmap doesn't work"
date: 2005-01-31
forum: General Help
---

### Post by Nuak on 2005-01-31
Hi all. nmap doesn't work for me in warty, nor in hoary.
If I try nmap -sP 192.168.2.0-254 as a normal user or as root I get the following:

```
Starting nmap 3.75 ( http://www.insecure.org/nmap/ ) at 2005-01-31 12:03 CET
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
Strange read error from 192.168.2.3: Transport endpoint is not connected
```

That repeats until I kill nmap with CTRL+C.
The network is running properly. I use 2.6.8.1 stock kernel in warty, and 2.6.10 kernel in hoary.
Hope you could help me.

---

