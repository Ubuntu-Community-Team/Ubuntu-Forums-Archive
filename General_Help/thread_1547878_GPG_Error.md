---
title: "GPG Error"
date: 2010-08-07
forum: General Help
---

### Post by energichen on 2010-08-07
GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
Any idea how to solve this?

---

### Post by dino99 on 2010-08-07
> **energichen said:**
> GPG error: [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
Any idea how to solve this?

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A8A515F046D7E7CF

[http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install](http://www.getdeb.net/updates/Ubuntu/10.04#how_to_install)

---

### Post by energichen on 2010-08-07
Thank you, that worked

---

