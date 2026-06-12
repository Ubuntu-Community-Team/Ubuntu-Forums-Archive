---
title: "Terminal*command*can't*find*files/folders"
date: 2010-04-17
forum: General Help
---

### Post by whaler1 on 2010-04-17
For some reason after a fresh 9.1 install I can't use cd or gedit from the terminal window.  I always get the same message 'No such file or directory'  

ie.
steve@Ubuntu:~$ sudo -s gedit '/etc/bash.bashrc' 
bash: sudo -s gedit /etc/bash.bashrc: No such file or directory

or
steve@Ubuntu:~$ cd '/media' 
bash: cd /media: No such file or directory

I have been using 8.1 for a year and have never had such a problem.  Is there something blatantly obvious that I am missing?

Many thanks,

---

### Post by whaler1 on 2010-04-18
It turns out this is a compatibility issue with a wireless driver.  Apparently when I activate my Broadcom 4357 wireless (installed via bcmwl-kernel-source package) it messes with Ubuntu 9.10.  If I deactivate the driver the problem goes away.  I will redirect this problem to the wireless discussions.

---

