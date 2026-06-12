---
title: "Maverick Repository Issue"
date: 2010-10-12
forum: General Help
---

### Post by Ingdawg on 2010-10-12
So a couple of days before the final release of Maverick, I installed the release candidate. I'm sort of an Ubuntu newbie, but I barely touched the system. All I did was keep it up-to-date. Every time I would reload the repositories in Synaptic, I would get this:
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192  
 

 W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release) 



This has happened since a fresh install. What's the deal?

---

### Post by DougieFresh4U on 2010-10-12
give this a try via terminal:
```
gpg –keyserver keyserver.ubuntu.com –recv 3E5C1192
gpg –export –armor 3E5C1192 | sudo apt-key add -
sudo apt-get update
```

---

### Post by Ingdawg on 2010-10-12
Thanks for the reply, but I'm getting the same the same error after trying that. What did that do by the way? It said it created keyrings and a new configuration file?

---

