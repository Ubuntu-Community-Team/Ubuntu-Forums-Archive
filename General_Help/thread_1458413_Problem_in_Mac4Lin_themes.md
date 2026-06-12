---
title: "Problem in Mac4Lin themes"
date: 2010-04-20
forum: General Help
---

### Post by i.arnav on 2010-04-20
The theme was installed in Ubuntu 9.04 fine. But theres a step which shows some errors in updating pachage

1. **sudo apt-get update**
2. sudo apt-get install gnome2-globalmenu

Runnung 1 shows error --> 
[I]
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D0AFF96872D340A3
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 7889D725DA6DEEAA[/I]

How do i solve this problem ?

---

### Post by labinnsw on 2010-04-22
Paste these command in a terminal

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com NO_PUBKEY D0AFF96872D340A3
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com NO_PUBKEY 632D16BB0C713DA6
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com NO_PUBKEY 7889D725DA6DEEAA
```

---

