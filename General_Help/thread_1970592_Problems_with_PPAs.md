---
title: "Problems with PPAs"
date: 2012-05-01
forum: General Help
---

### Post by TurtleKing on 2012-05-01
Not exactly sure how to fix them (Google didn't help).
```
W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
```

---

### Post by sgage on 2012-05-01
> **TurtleKing said:**
> Not exactly sure how to fix them (Google didn't help).
```
W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/precise/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/precise/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/slicer/ppa/ubuntu/dists/precise/main/binary-i386/Packages  404  Not Found
```

Some ppa's create repos for a new release right away, or even pre-release. Some lag. You could try editing them and substituting 'oneiric' for 'precise' - it often works. Or just wait.

---

### Post by jerrrys on 2012-05-01
Sgage is probably right, but you could try changing download source.  May get lucky.

---

### Post by TurtleKing on 2012-05-03
I'm just going to re-install Ubuntu, as update manager is still taking 30 seconds to update the package list (1 week after release?)

---

### Post by Cheesemill on 2012-05-03
> **TurtleKing said:**
> I'm just going to re-install Ubuntu, as update manager is still taking 30 seconds to update the package list (1 week after release?)
That wont make any difference, the servers are all still slow.

---

