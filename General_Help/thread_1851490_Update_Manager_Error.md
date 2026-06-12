---
title: "Update Manager Error"
date: 2011-09-28
forum: General Help
---

### Post by anishbalan on 2011-09-28
Hi All,

Please help me solve this problem.

I have Ubuntu 11.04 installed in my PC. A couple of dates back, all of a sudden the update manager stated showing problem. First, updates were showing up. When I was trying to installing updates, it was showing "Internet Connection error". Now no updates are showing up. When I checked for updates, it gives me an error "Failed to download repository Information". On the details log, it is showing: 
W:Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by 2F4U on 2011-09-28
Maybe the mirror you are trying to download from is down. Try switching to another mirror.

---

### Post by plucky on 2011-09-28
> **anishbalan said:**
> Hi All,

Please help me solve this problem.

I have Ubuntu 11.04 installed in my PC. A couple of dates back, all of a sudden the update manager stated showing problem. First, updates were showing up. When I was trying to installing updates, it was showing "Internet Connection error". Now no updates are showing up. When I checked for updates, it gives me an error "Failed to download repository Information". On the details log, it is showing: 
W:Failed to fetch [http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages](http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```
http://za.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-i386/Packages

```

Open Software Sources and delete the repository that is pointing to **Jaunty**

Good Luck

---

