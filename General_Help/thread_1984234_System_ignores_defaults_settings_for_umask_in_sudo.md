---
title: "System ignores defaults settings for umask in sudoers"
date: 2012-05-21
forum: General Help
---

### Post by ze_otter on 2012-05-21
I've been trying to set up my sudo so that while I as a user use umask 0077, sudo would use 0022. To achieve this, I put these two lines in using visudo:

```
Defaults umask_override
Defaults umask=0022
```

However, creating a file with sudo still creates them using my user umask 0077 so it seems as if the system is ignoring those lines. What could be wrong? I'm still using 10.04 until they release the 12.04.1 - possible bug in sudo in this release?

---

