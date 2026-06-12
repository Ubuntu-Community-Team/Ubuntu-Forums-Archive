---
title: "Some strange and scary error."
date: 2011-06-13
forum: General Help
---

### Post by colobix on 2011-06-13
How do I fix this. Is it something to worry about or can I just ignore it?

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures could not be verified because the public key is not available: NO_PUBKEY 504B59436C3321F2

---

### Post by nothingspecial on 2011-06-13
Hi, type this in a terminal

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 504B59436C3321F2
```

---

### Post by colobix on 2011-06-13
Thanks a lot. That worked:)

---

