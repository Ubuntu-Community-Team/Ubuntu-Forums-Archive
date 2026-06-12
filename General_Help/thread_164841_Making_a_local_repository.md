---
title: "Making a local repository"
date: 2006-04-23
forum: General Help
---

### Post by Teh Ethan on 2006-04-23
I'd like to make a local apt repository so I can update a bunch of machines (25+) without having to download all the packages from the internet each time. I was thinking about using a server to cache the packages; is this how you do it?

**Server** ```
apt-get -d update && apt-ftparchive packages ./ ./Packages && gzip ./Packages
```**Clients**```
echo 'deb http://12.34.56.78/ packages/' >> /etc/apt/sources.list
```(Ignoring sudo's and stuff)

---

### Post by aysiu on 2006-04-23
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

---

### Post by Wolki on 2006-04-23
There's also apt-proxy, you won't need cds for this.

Homepage: [http://apt-proxy.sourceforge.net/](http://apt-proxy.sourceforge.net/)
Ubuntu tutorial: [https://wiki.ubuntu.com/AptProxyHowTo](https://wiki.ubuntu.com/AptProxyHowTo)

---

