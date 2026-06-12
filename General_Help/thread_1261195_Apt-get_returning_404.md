---
title: "Apt-get returning 404"
date: 2009-09-08
forum: General Help
---

### Post by jranson on 2009-09-08
Hey all, I'm using Ubuntu 8.04 Server LTS. When I try to apt-get install wine, I'm getting the following error: 

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.7-10ubuntu4_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i386_2.7-10ubuntu4_amd64.deb)  404 Not Found [IP: 91.189.88.46 80]

I have checked the archive and indeed there is not ubuntu4 package of the libc6, only 3 and 5. How can I go about resolving this?

---

### Post by philinux on 2009-09-08
Have you added a ppa to get wine if so this is where the dependency problem could occur.

---

### Post by jranson on 2009-09-10
Hi Phil, I'm not sure what a PPA is, so I'm going to go with No. This is an out of the box Ubuntu install with no customizations and literally the first thing I've tried to do is sudo apt-get install wine, and am getting this error.

---

