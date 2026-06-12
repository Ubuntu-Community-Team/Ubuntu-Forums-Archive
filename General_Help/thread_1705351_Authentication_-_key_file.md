---
title: "Authentication - key file"
date: 2011-03-12
forum: General Help
---

### Post by phh on 2011-03-12
Anyone know what this output from "apt-get update" is about? (Can't see any reference to it in my Software Sources/Authentication tab.)

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7E8C913A99AA8CD6

---

### Post by oldos2er on 2011-03-12
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 7E8C913A99AA8CD6
```

---

