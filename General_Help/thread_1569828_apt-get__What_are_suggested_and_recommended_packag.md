---
title: "apt-get:  What are suggested and recommended packages?"
date: 2010-09-07
forum: General Help
---

### Post by halfpower on 2010-09-07
When I use apt-get to install a package it lists suggested packages.  These packages aren't required dependencies.  Why are they suggested?  Is there something else called a recommended package?  If so, how does it differ from a suggested package?

---

### Post by gzarkadas on 2010-09-07
'Recommended' packages are packages that though not necessary for the package to work, provide additional functionality which many users would wanted.

'Suggested' packages are a more weak dependency than recommended packages. They provide additional functionality useful to a smaller base of users.

See for details: [http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_package_dependencies](http://www.debian.org/doc/manuals/debian-reference/ch02.en.html#_package_dependencies)

Both of the above are optional and thus not automatically picked-up by apt-get. But you could pipe the apt-get's output to `| tee [logfile]' and then grep the logfile for those keywords to bring in surface all those related packages and, if you like, install them.

---

