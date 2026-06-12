---
title: "How big is your /usr folder"
date: 2010-07-11
forum: General Help
---

### Post by needhelppeeps on 2010-07-11
My /usr folder is at 2.3 gb. I am thinking this might be excessive, looking for typical installation to compare to. I only have a handfull of apps installed. About half of it is in /usr/lib... I am thinking there must be a lot of junk in there that needs cleaned up.

---

### Post by Tom Dignan on 2010-07-11
You might be able to free up some space by removing orphaned dependencies. Install deborphan and try it.

---

### Post by daniel_w93 on 2010-07-11
I dont know how long have you been using your system, but if you've installed and uninstalled a lot of stuff it always leaves some useless junk (most of them .lib files) 
dont clean it up manually though! use

```
sudo apt-get autoremove
```

---

