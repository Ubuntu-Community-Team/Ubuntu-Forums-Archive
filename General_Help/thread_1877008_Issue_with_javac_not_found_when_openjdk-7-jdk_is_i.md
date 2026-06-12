---
title: "Issue with javac not found when openjdk-7-jdk is installed!"
date: 2011-11-07
forum: General Help
---

### Post by M1GEO on 2011-11-07
Hi all.

The title pretty well sums this up. I am trying to 'compile' some Java code using *javac*.  However, I get some interesting results; This is on Ubuntu 11.10.

I try and run javac:
```
george@georgesmartbox:~$ javac
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.6-jdk
 * gcj-4.5-jdk
 * openjdk-7-jdk
Try: sudo apt-get install <selected package>
```

So I try and install *openjdk-7-jdk*:
```
sudo apt-get install openjdk-7-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-7-jdk is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 36 not upgraded.
```

So it tells me that it's already the newest version?  I'm not sure how to fix this.

Any advice would be great.
Thanks.

---

### Post by M1GEO on 2011-11-07
For completeness, I found these instructions & script that install the official Oracle Java DevKit on 11.10, so I went with that.

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

