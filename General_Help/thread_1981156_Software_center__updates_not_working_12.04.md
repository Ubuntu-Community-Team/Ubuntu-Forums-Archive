---
title: "Software center / updates not working 12.04"
date: 2012-05-16
forum: General Help
---

### Post by sictiburon on 2012-05-16
Hey folks, yesterday i updated my ubuntu version (from scratch) on my laptop to the 12.04. Everything was working perfect until today, i've been trying to use the software center and every time it gives me an error. Also i'm trying to install this using the terminal:
sudo apt-get install python-glade2

but it gives me this error:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  python-gtk2-doc
The following NEW packages will be installed:
  python-glade2
0 upgraded, 1 newly installed, 0 to remove and 24 not upgraded.
Need to get 9,870 B of archives.
After this operation, 116 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  python-glade2
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main python-glade2 i386 2.24.0-3
  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygtk/python-glade2_2.24.0-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pygtk/python-glade2_2.24.0-3_i386.deb)  Something wicked happened resolving 'us.archive.ubuntu.com:http' (-5 - No address associated with hostname)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Please help!

---

### Post by parajulik on 2012-05-16
Can you access this webpage ([http://us.archive.ubuntu.com/](http://us.archive.ubuntu.com/)) using your web browser (from your Ubuntu laptop)?

---

### Post by sictiburon on 2012-05-16
Yes parajulik, i can access the page you told me (with my ubuntu laptop)

---

### Post by parajulik on 2012-05-16
I would try a different mirror than us.archive.ubuntu.com. Here are the instructions to change to a different download server: [https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

---

### Post by sictiburon on 2012-05-16
I'll try that bro

---

