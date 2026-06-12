---
title: "I can't update"
date: 2011-11-06
forum: General Help
---

### Post by CinoxFellpyre on 2011-11-06
W:Failed to fetch [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/source/Sources)  404  Not Found , W:Failed to fetch [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404  Not Found [IP: 91.189.92.181 80] , W:Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.181 80] , E:Some index files failed to download. They have been ignored, or old ones used instead.  Is it just me, or are others getting this too?

---

### Post by raja.genupula on 2011-11-07
1....update manager -> settings --> change your server to other mirror and try again.

2....or update manager and settings other software and unselect that particular ppa's.

all the best

---

### Post by CinoxFellpyre on 2011-11-07
Chose another server, got the same thing  Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources)  404  Not Found [IP: 91.189.92.171 80] Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.92.171 80] Failed to fetch [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/source/Sources)  404  Not Found Failed to fetch [http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by plucky on 2011-11-07
```
http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources

```

Jaunty repository is no longer open/supported.Disable in Software Sources all references to Jaunty

```
http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/natty/main/source/Sources
```

There is no PPA for Natty,again remove from Software Sources.

See [Here](http://ppa.launchpad.net/adamkoczur/gtk1.2/ubuntu/dists/)


Good Luck

---

### Post by CinoxFellpyre on 2011-11-07
I thought that was the case, so I nuked them.  No more problem :3

---

