---
title: "problem updating ubuntu"
date: 2011-08-30
forum: General Help
---

### Post by dyaddaw on 2011-08-30
hi.  problem when updating ubuntu.  in the terminal I get the following message during the update 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_natty-security_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

not sure if this is related to me not being able to search and install new software as well.
Darryl

---

### Post by kyletstrand on 2011-08-31
Try this:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Seems to have worked quite well for others receiving the same error.

---

