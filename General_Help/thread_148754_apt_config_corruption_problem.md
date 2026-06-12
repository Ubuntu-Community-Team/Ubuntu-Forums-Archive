---
title: "apt config corruption problem"
date: 2006-03-22
forum: General Help
---

### Post by Michael Matthews on 2006-03-22
I ran some apt script that was for dapper and screwed up my breezy apt. How can I clean it up? I get this error message for all apt commands:

E: Could not open file /var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_Release - open (13 Permission denied)
E: Could not open file /var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_Release.gpg - open (13 Permission denied)

There is no such file as far as I can see. apt must be creating it on the fly based on some miss configuration.
/etc/apt/sources.list is OK

How do I clear this out?

---

