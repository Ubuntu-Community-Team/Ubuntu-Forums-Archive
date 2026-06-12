---
title: "apt-mirror and net installer-amd64 files"
date: 2011-03-16
forum: General Help
---

### Post by boomboom69 on 2011-03-16
I am using apt-mirror to create a local mirror of only Lucid and Maverick, and have created a xen XCP cloud. When I try to create a VM in the cloud for ubuntu using xen template for ubuntu 10.04 and point it to my mirror for netinstallation I get an error missing file in /main/installer-amd64/etc.... I have added main/debian-installer to my apt-mirror list but it doesn't get the main/installer-amd64 files. If I try to add that, apt-mirror complains that it can't find binary-amd64 in there. How do I get apt-mirror to download the main/installer-amd64 files?

---

