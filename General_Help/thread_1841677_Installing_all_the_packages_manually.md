---
title: "Installing all the packages manually"
date: 2011-09-09
forum: General Help
---

### Post by tech291083 on 2011-09-09
Hi Friends,

I have one desktop pc at home with no internet access, but I have installed Ubuntu 10.10 on it. How can I install, upgrade, update packges? I have internet access at work and can download packages there on a pc and then bring them home on a USB pen drive. But can I install all the packages that I am going to need in this manner ie manually? Is it possible to use Ubuntu on a pc with no internet access at all? Here is a page that lists packages for Ubuntu 10.10 and I am not sure whether I can find all the compatible packages here. But I am sure that I will atleast get the most common ones. I really need some help as I would love to use Ubuntu on that pc. Please help. Thanks.

[http://packages.ubuntu.com/maverick/](http://packages.ubuntu.com/maverick/)

---

### Post by JC Cheloven on 2011-09-09
Hi, I'd say you need aptoncd. 
As usual, the Ubuntu contributed documentation is a great source of information to read about this, and related topics:

[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)
[https://help.ubuntu.com/10.04/add-applications/C/offline.html](https://help.ubuntu.com/10.04/add-applications/C/offline.html)
[https://help.ubuntu.com/community/Synaptic/Offline](https://help.ubuntu.com/community/Synaptic/Offline)

Also, the .deb packages of everything you installed are stored in /var/cache/apt/archives, but you'll probably not need to use that. Again: aptoncd.

Cheers
JC

---

