---
title: "How to fail dpkg installation from postinst?"
date: 2009-07-06
forum: General Help
---

### Post by jillmashley on 2009-07-06
I have created a .deb package to install some software and would like to fail the whole installation if something goes wrong from within postinst. However, exiting postinst with some code other than 0 does not seem to fail the package installation (either using dpkg or apt directly to install), and the package state is installed when the installation completes. Any ideas?

Thanks!

---

