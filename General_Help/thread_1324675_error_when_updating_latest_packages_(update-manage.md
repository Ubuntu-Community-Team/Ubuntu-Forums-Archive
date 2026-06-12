---
title: "error when updating latest packages (update-manager + python packages)"
date: 2009-11-12
forum: General Help
---

### Post by manolo_asdf on 2009-11-12
hi, with latest karmic update through update manager i receive:

-----------------------
W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/libpython2.6_2.6.4-0ubuntu1_i386.deb)
  404  Not Found [IP: 141.76.2.134 80]


W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.4-0ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6_2.6.4-0ubuntu1_i386.deb)
  404  Not Found [IP: 141.76.2.134 80]


W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.4-0ubuntu1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/p/python2.6/python2.6-minimal_2.6.4-0ubuntu1_i386.deb)
  404  Not Found [IP: 141.76.2.134 80]


W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.126.6.1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.126.6.1_all.deb)
  404  Not Found [IP: 141.76.2.134 80]


W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.126.6.1_i386.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.126.6.1_i386.deb)
  404  Not Found [IP: 141.76.2.134 80]
------------------


there seem to be missing packages on server (404 http status). has somebody received similar and could resolve it?

---

### Post by Andysan on 2009-11-22
Hi,

I had the same problem - [changing to a different mirror ]("http://www.packtpub.com/article/ubuntu-9.10-how-to-upgrade")fixed it for me.  It's about halfway down the page.

Cheers.

---

