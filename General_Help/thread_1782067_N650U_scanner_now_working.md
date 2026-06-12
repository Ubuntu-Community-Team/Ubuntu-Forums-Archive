---
title: "N650U scanner now working"
date: 2011-06-14
forum: General Help
---

### Post by pouldney on 2011-06-14
My canon N650U scanner is now working
Apparently it requires plustek_pp driver

sudo gedit /etc/sane.d/dll.conf
remove # from in front of plustek_pp
  re-boot

then use xsane frontend  (use synaptic package manager to install it)
It works better than simple scan

---

