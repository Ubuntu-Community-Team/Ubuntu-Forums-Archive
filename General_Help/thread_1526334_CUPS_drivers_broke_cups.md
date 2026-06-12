---
title: "CUPS drivers broke cups"
date: 2010-07-07
forum: General Help
---

### Post by Leppie on 2010-07-07
i installed the 1.4.4 drivers from the cups site, but after cups does not start anymore.
i get the error:
```
cupsd: Child exited with status 127!
cups: unable to restart scheduler.
```
and with -f i get the folowing messge:
```
sudo cupsd -f
cupsd: symbol lookup error: cupsd: undefined symbol: _pwgDestroy
```

all help and suggestions much appreciated.

---

### Post by jcpeden on 2011-05-09
Exact same problem for me. The CUPS admin page is not accessible on server:631 and I get the exact same message as you when I try to restart cups.

That **last** thing I did to my CUPS installation was to setup a printer driver dump to enable Windows PCs to automatically install drivers for my two CUPS printers shared in Samba. The setup was working absolutely perfectly yesterday and today when I booted up the server, CUPS would not start.

I've tried playing around with smb.conf to no avail and restored an older version of cupsd.conf with no luck.

---

