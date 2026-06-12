---
title: "Building deb of bash scripts"
date: 2012-01-13
forum: General Help
---

### Post by Hiisi on 2012-01-13
Hi, forum!
I want to build my own deb-package to carry on routine work (initial setup of user' workstations). The package consists of a few configs and a bash script. But before putting configs to /etc directory I need all the necessary packages to be installed. Hence in config file of my package I have the following entry:
Depends: vim, subversion, cmake, ...etc
I can build a deb out of it but during installation using apt-get the output consists of errors like following:
E: Release 'my_package_name' for 'tickr' was not found
What the heck with it??

---

