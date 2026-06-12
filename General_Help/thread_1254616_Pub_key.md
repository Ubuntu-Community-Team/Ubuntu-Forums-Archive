---
title: "Pub_key"
date: 2009-08-31
forum: General Help
---

### Post by xdweaver on 2009-08-31
I need to know how to fix this: 

W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7D2C7A23BF810CD5
W: GPG error: [http://ppa.launchpad.net]("http://ppa.launchpad.net/") jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3B22AB97AF1CDFA9


please help

---

### Post by sisco311 on 2009-08-31
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BF810CD5
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys AF1CDFA9
```

[https://launchpad.net/+help/soyuz/ppa-sources-list.html]("https://launchpad.net/+help/soyuz/ppa-sources-list.html")

---

