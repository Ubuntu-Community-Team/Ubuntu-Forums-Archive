---
title: "sources.list errors"
date: 2009-11-20
forum: General Help
---

### Post by HavocXphere on 2009-11-20
Hi

I want to add a [specific local mirror]("deb ftp://ftp.is.co.za/mirrors/ftp.ubuntu.com/archive/ubuntu/dists/") to grab ubuntu updates from.

**_sources.list_**
```
deb ftp://ftp.is.co.za/mirrors/ftp.ubuntu.com/archive/ubuntu/dists/ jaunty main
```
(I realize I need the others too...just want to get main working first)

**_Error Received_**
```
Failed to fetch ftp://ftp.is.co.za/mirrors/ftp.ubuntu.com/archive/ubuntu/dists/dists/jaunty/main/binary-amd64/Packages  Unable to fetch file, server said '/mirrors/ftp.ubuntu.com/archive/ubuntu/dists/dists/jaunty/main/binary-amd64/Packages: No such file or directory  '
```

I'm reasonably sure the server is configured correctly. I've checked and there is a packages.gz file there and it is accessible via browser. However the error message leaves out the .gz part so maybe thats the problem?

Bonus Question: Can one list multiple components in one line? i.e. main multiverse universe restricted

Thanks

---

