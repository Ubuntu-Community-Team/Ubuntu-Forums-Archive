---
title: "Samba update not working"
date: 2010-03-25
forum: General Help
---

### Post by Warthaug on 2010-03-25
Ubuntu is trying to update samba as part of its usually-scheduled updates.  However, this is failing due to dependency problems.  I've tried selecting the mis-behaving packages in synaptic for re-install, but that generates the same error.  I was hoping someone would know how to fix the problem.  The error:

> E: samba-common: subprocess installed post-installation script returned error exit status 10
E: samba: dependency problems - leaving unconfigured
E: samba-common-bin: dependency problems - leaving unconfigured
E: smbclient: dependency problems - leaving unconfigured

I cannot seem to copy the details of the error, but the "terminal" screen of the install box basically shows a circular set of dependencies: samba requires smbclient, which in turn requires samba, etc.  The end effect being nothing gets install, since each package seems to need the other ones installed first.

Bryan

---

