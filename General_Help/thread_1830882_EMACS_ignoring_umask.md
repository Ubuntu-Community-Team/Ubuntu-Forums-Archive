---
title: "EMACS ignoring umask"
date: 2011-08-22
forum: General Help
---

### Post by hebetude on 2011-08-22
When I create files with EMACS, it is creating files with permission 600, despite my default umask 022.  

This is becoming particularly troublesome with the p4 plugin, because when editing/commiting file the permissions are changed to 600 again.  Possibly it is deleting and writing the file, and making the files unreadable by other users/groups.      

How do I change the default umask of EMACS to use 022?

---

