---
title: "Apt pinning with apt-build not working as expected"
date: 2009-07-09
forum: General Help
---

### Post by zak on 2009-07-09
I built my own X server packages so I could use fglrx with an R500 on Jaunty. I want to keep those and never upgrade, so I've pinned all apt-build packages. The only problem is, it doesn't work

```

$ cat /etc/apt/preferences 
Package: *
Pin: release a=apt-build
Pin-Priority: 900

$ apt-cache policy xserver-xorg
xserver-xorg:
  Installed: 1:7.4~5ubuntu3
  Candidate: 1:7.4~5ubuntu18
  Version table:
     1:7.4~5ubuntu18 0
        500 http://archive.ubuntu.com jaunty/main Packages
     1:7.4~5ubuntu3 0
        500 http://archive.ubuntu.com intrepid/main Packages
     1:7.4~5ubuntu3 0
        500 file: apt-build/main Packages
 *** 1:7.4~5ubuntu3 0
        100 /var/lib/dpkg/status

```

---

