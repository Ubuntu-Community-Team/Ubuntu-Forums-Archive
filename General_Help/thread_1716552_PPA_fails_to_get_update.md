---
title: "PPA fails to get update"
date: 2011-03-28
forum: General Help
---

### Post by SJ2011 on 2011-03-28
Hello, everyone. I am a newbie. Recently, I tried to install the following PPA "ppa:alexeftimie/ppa" However, it just failed to download/fetch the files needed to finish installation.Please see below.Also, I can not receive any updates at all. Thank you in advance!

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages             
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages
  404  Not Found
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Get:5 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [1,096B]                  
Get:6 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [737B]                    
Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter

<enter>

Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/main i386 Packages/DiffIndex
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007) maverick/restricted i386 Packages/DiffIndex
Fetched 4,921B in 5min 31s (15B/s)
W: Failed to fetch [http://ppa.launchpad.net/Alexeftimie/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/Alexeftimie/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/Alexeftimie/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/Alexeftimie/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by r-senior on 2011-03-28
In the short term, to get your updates running, you can disable the PPA in Software Sources. Just untick the box that's causing the problem and you should be OK again.

Why the PPA is not there (and I clicked on the link and got "Not Found" too), I don't know. Has it ever worked?

---

### Post by SJ2011 on 2011-03-28
Thank you r-senior for the help! No, the link has never worked for me. However, I am still getting the following message when I try to get updates using the Update Manager. Please see the attachment. How do I resolve this issue(s)? Why am I getting this message everytime I update?

Thank you

---

### Post by plucky on 2011-03-29
> **SJ2011 said:**
> Thank you r-senior for the help! No, the link has never worked for me. However, I am still getting the following message when I try to get updates using the Update Manager. Please see the attachment. How do I resolve this issue(s)? Why am I getting this message everytime I update?

Thank you

Un-tick the CDrom as a source in **Software Sources**

If that doesn't work,please post the output from a terminal of ```
cat /etc/apt/sources.list
```


The PPA does not have a maverick repository. See [Here](http://ppa.launchpad.net/alexeftimie/ppa/ubuntu/dists/)

Also Alexeftimie should be alexeftimie as linux is case sensitive.

Good Luck

---

### Post by SJ2011 on 2011-03-29
Thank you plucky for the help, it worked. This is a slow learning process.

---

