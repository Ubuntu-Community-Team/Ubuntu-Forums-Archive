---
title: "some ppa problems and ATI card driver help"
date: 2012-05-09
forum: General Help
---

### Post by athalsten on 2012-05-09
i am a new user of ubuntu, just using from few days. and love it too much for its speed
i have two problems

1st
when i add some ppa this errors ocurd when i update 
> 
W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D6B6DB186A68F637, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

and 2nd
i downloaded the ati driver from the website but cant install it , it is a .run file how to install it . i put it desktop

plz help any one

---

### Post by Enigmapond on 2012-05-09
Well the first problem is a public key issue. The best way to add a ppa is go to the page and about mid-way on the left side you will see in bold letters, "ppa:whatever the name/ppa add this to:

```
sudo add-apt-repository
```

in the terminal. That will import the public key.

---

### Post by lukeiamyourfather on 2012-05-09
Don't use graphics drivers from the manufacturer website. Use the "Additional Drivers" utility in Ubuntu which will cleanly install the same driver in such a way that it can be removed if needed. Binary drivers directly from the manufacturer make a real mess of the system and can't be removed cleanly.

---

### Post by athalsten on 2012-05-09
> **Enigmapond said:**
> Well the first problem is a public key issue. The best way to add a ppa is go to the page and about mid-way on the left side you will see in bold letters, "ppa:whatever the name/ppa add this to:

```
sudo add-apt-repository
```in the terminal. That will import the public key.


thanks tryed it but still this happened

> W:GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D6B6DB186A68F637, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-clamav/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

maybe the ppa is dead?

---

### Post by athalsten on 2012-05-09
> **lukeiamyourfather said:**
> Don't use graphics drivers from the manufacturer website. Use the "Additional Drivers" utility in Ubuntu which will cleanly install the same driver in such a way that it can be removed if needed. Binary drivers directly from the manufacturer make a real mess of the system and can't be removed cleanly.


thanks i will try it

---

