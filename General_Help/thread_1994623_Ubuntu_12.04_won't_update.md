---
title: "Ubuntu 12.04 won't update"
date: 2012-06-03
forum: General Help
---

### Post by amarumayo on 2012-06-03
Hi all, when I run the update it installs most of the packages then it kills itself with this message:

Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center-data_3.4.1-0ubuntu2_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center-data_3.4.1-0ubuntu2_all.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-control-center1_3.4.1-0ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-control-center1_3.4.1-0ubuntu2_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_3.4.1-0ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_3.4.1-0ubuntu2_i386.deb) 404  Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.2.2.1_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/s/software-center/software-center_5.2.2.1_all.deb) 404  Not Found

How do I fix this so that I can update my system?
I have Ubuntu 12.04 w/unity

Many thanks
c

---

### Post by dino99 on 2012-06-03
switch to an other mirror, or use "main"

---

### Post by sanderj on 2012-06-03
The software-center_5.2.2.1_all.deb is not available on that URL, but a more recent version (software-center_5.2.2.2_all.deb) is, so:


```
sudo apt-get update
sudo apt-get upgrade

```

HTH

---

### Post by amarumayo on 2012-06-03
yeah that did the trick
thanks

---

### Post by sanderj on 2012-06-03
> **amarumayo said:**
> yeah that did the trick
thanks

Which of the two advices did the trick?

---

### Post by amarumayo on 2012-06-03
Apologies, the first bit of advice worked. i.e. switch to an other mirror, or use "main"

---

