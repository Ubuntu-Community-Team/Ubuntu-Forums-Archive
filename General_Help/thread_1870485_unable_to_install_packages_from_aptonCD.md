---
title: "unable to install packages from aptonCD"
date: 2011-10-27
forum: General Help
---

### Post by cool_techie on 2011-10-27
Hello,
      I made an apton Cd of Ubuntu 11.10 with some packages in there.
      When I try to install those those packages on my system(ubuntu 11.10) I am unable to do so. It shows download via normal software channels and doesn't give me install option.
Similar is the case with all .deb files I downloaded and tried to install.
Please help.

---

### Post by Gremlinzzz on 2011-10-27
[https://help.ubuntu.com/8.04/add-applications/C/offline.html](https://help.ubuntu.com/8.04/add-applications/C/offline.html)
:popcorn:



[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

---

### Post by ajgreeny on 2011-10-27
You need aptoncd on the destination machine as well as the source machine to do it that way.

You can, however, do the job just as easily by manually copying the .deb files from var/cache/apt/archives in the source to /var/cache/apt/archives in the destination using a flash drive, and then installing or updating with synaptic, which is how I do it now;  much faster than aptoncd.

---

