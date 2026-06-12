---
title: "Server Error"
date: 2009-07-07
forum: General Help
---

### Post by seangraph on 2009-07-07
```
LANG=C aptitude reinstall cacti-cactid
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  cacti-cactid
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up cacti-cactid (0.8.6g-1build1) ...
dpkg: error processing cacti-cactid (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 cacti-cactid
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up cacti-cactid (0.8.6g-1build1) ...
dpkg: error processing cacti-cactid (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 cacti-cactid
```

This is the error that my server replay to me my site is under him [www.phentermine-hcl.net]("http://www.phentermine-hcl.net")

can someone explain me what does it mean?

thanks

---

### Post by Ryadt on 2009-07-07
Try ```
sudo apt-get -f install
```

---

