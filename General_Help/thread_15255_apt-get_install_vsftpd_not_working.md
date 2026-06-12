---
title: "apt-get install vsftpd not working"
date: 2005-02-13
forum: General Help
---

### Post by OOmiz on 2005-02-13
I have a problem with installing vsftpd. I could download the source and compile it from their official homepage but I still want to know why apt-get isn't working.

```
root@kilpkonn:/home/oomiz # apt-get install vsftpd
Reading Package Lists... Done
Building Dependency Tree... Done
Package vsftpd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package vsftpd has no installation candidate
``` 

Have I missed something?

All lines in /etc/apt/sources.list are uncommented. No other problems with apt-get. Sadly I cannot run the package manager in gnome since I'm using icewm. (low-end system)

*edit* reinstalled linux... it's working now

---

