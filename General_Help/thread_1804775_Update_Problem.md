---
title: "Update Problem"
date: 2011-07-15
forum: General Help
---

### Post by suresh_r on 2011-07-15
Hi, i am quite new to linux....

i keep getting this when i run update...please help

W:Failed to fetch [http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/alexftimie/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ajgreeny on 2011-07-15
Go to **system-administration-software sources** (not sure how you get there in unity, but I'm sure you'll find it) and in the **other software** tab remove that ppa from the list.  I don't think it exists any more so is no good for you now. Then reload the cache list and all should be well.

---

### Post by raja.genupula on 2011-07-15
hey man run this

```
 sudo rm -rf /var/lib/apt/lists/*
```
```
sudo apt-get update
```



it will be cleared , i am sure . if solve please make the thread as solved .

---

### Post by suresh_r on 2011-07-19
Hey Raja, that didn't work....still showing the same error, so i remove the entire PPA addresses from "OTHER SOFTWARE" in the update manager?

---

