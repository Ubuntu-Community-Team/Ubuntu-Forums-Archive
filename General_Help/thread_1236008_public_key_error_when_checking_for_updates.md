---
title: "public key error when checking for updates"
date: 2009-08-09
forum: General Help
---

### Post by stlnative on 2009-08-09
Every time I check for updates after upgrading to the latest version I get this error message:


W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY B152F042D246C25D



how do I correct this problem

---

### Post by michy99 on 2009-08-09
Run this in a terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys D246C25D
```

---

