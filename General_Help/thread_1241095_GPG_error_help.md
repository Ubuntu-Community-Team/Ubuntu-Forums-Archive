---
title: "GPG error help"
date: 2009-08-15
forum: General Help
---

### Post by sports fan Matt on 2009-08-15
Can someone help me remedy this or help me find the right key?  

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60D11217247D1CFF

---

### Post by michy99 on 2009-08-15
Run this in a terminal:```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 247D1CFF
```

---

