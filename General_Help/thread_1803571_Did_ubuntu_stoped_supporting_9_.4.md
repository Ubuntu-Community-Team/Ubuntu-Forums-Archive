---
title: "Did ubuntu stoped supporting 9 .4 ?"
date: 2011-07-13
forum: General Help
---

### Post by lion21 on 2011-07-13
Did ubuntu removed files for 9.4 repository from there server coause when I do 

> sudo apt-get update 

I get following warnings 


> 2098A6E
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/jaunty-security/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/jaunty-security/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/jaunty-security/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.166 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/binary-amd64/Packages.gz)  404 Not Found [IP: 91.189.92.171 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.92.171 80]


My O.S info
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

---

### Post by sanderd17 on 2011-07-13
See the version timeline: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

The support for Ubuntu 9.04 has stopped in October 2010. You should upgrade: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

PS Put code in CODE tags, not in QUOTE tags

---

### Post by lion21 on 2011-07-13
> **sanderd17 said:**
> See the version timeline: [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)

The support for Ubuntu 9.04 has stopped in October 2010. You should upgrade: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

PS Put code in CODE tags, not in QUOTE tags

thanks very much I shd be upgrading nw.

---

### Post by CatKiller on 2011-07-13
> **lion21 said:**
> Did ubuntu removed files for 9.4 repository from there server

Yes. FWIW, you can continue to install packages in no-longer-supported versions of Ubuntu, you just need to change your repositories to point to old-releases.ubuntu.com instead. No more security updates, though, which is why it's a good idea to upgrade.

---

