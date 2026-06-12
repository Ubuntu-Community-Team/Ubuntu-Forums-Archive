---
title: "CK-Kernel patchset on linux 3.5-rc7?"
date: 2012-07-16
forum: General Help
---

### Post by Argenteus on 2012-07-16
I've heard the ck kernel patchset can improve performance on many systems. However, although 3.5-rc7 appears to be the latest kernel, it says to patch 3.4. Is there a patch available for the latest kernel, or will the old one work? Thanks.

---

### Post by idoitprone on 2012-07-16
> **Argenteus said:**
> I've heard the ck kernel patchset can improve performance on many systems. However, although 3.5-rc7 appears to be the latest kernel, it says to patch 3.4. Is there a patch available for the latest kernel, or will the old one work? Thanks.

it does not improve performance, it changes the cpu scheduler to bfs which decreases latency to improve perceived performance.
the 3.5 kernel is not out yet, i doubt that he has the patches ready

compiling is a pain use a ppa
[https://launchpad.net/~chogydan/+archive/ppa]("https://launchpad.net/%7Echogydan/+archive/ppa")
```
 sudo add-apt-repository ppa:chogydan/ppa && sudo apt-get update
sudo apt-get install linux-image-generic-ck linux-headers-generic-ck

```this will only be good on systems with cpus less than 16 cores.

---

### Post by Argenteus on 2012-07-17
> **idoitprone said:**
> it does not improve performance, it changes the cpu scheduler to bfs which decreases latency to improve perceived performance.
the 3.5 kernel is not out yet, i doubt that he has the patches ready

compiling is a pain use a ppa
[https://launchpad.net/~chogydan/+archive/ppa]("https://launchpad.net/%7Echogydan/+archive/ppa")
```
 sudo add-apt-repository ppa:chogydan/ppa && sudo apt-get update
sudo apt-get install linux-image-generic-ck linux-headers-generic-ck

```this will only be good on systems with cpus less than 16 cores.

3.5 may not be at a stable release yet, but kernel.org clearly has a download for it, and I like using the newest, most cutting edge software. And compiling offers more flexibility than using a ppa. Also, I certainly have less than 16 cores, this is a netbook.

---

### Post by idoitprone on 2012-07-17
> **Argenteus said:**
> 3.5 may not be at a stable release yet, but kernel.org clearly has a download for it, and I like using the newest, most cutting edge software. And compiling offers more flexibility than using a ppa. Also, I certainly have less than 16 cores, this is a netbook.

this might improve performance due to the fact that it uses less resources than the mainline scheduler

---

