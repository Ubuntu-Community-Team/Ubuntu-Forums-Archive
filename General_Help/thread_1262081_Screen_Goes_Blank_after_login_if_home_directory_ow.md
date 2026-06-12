---
title: "Screen Goes Blank after login if home directory owner is different"
date: 2009-09-09
forum: General Help
---

### Post by a_artha on 2009-09-09
Our Environment is 
250 Ubuntu 9.04 Desktop, 2 Ltsp Servers with 60 thin clients shared by 1500 students for their laboratory purpose for the past two years very fine.
All are authenticated using NIS
The Home directory is on NFS mounted using automounter.

Now i face a problem. Frequently studens change the permissions of their home directory and creating lot of nuisance.

So I implemented Acl on their home directory with root as owner and the actual owner having rwx permission with rwx as mask. others don't have access to that folder.

For SSH login this setup is working fine.

when the student login using gnome or kde the screen goes black with mouse pointer is working. nothing happend after that.

If they use gnome failsafe session, working fine.

Instead of keeping home directory on nfs i placed it on the local hard disk with same acl permission said above. I got the same error.

Pl help me

---

