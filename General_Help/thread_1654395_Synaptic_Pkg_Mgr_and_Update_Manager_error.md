---
title: "Synaptic Pkg Mgr and Update Manager error"
date: 2010-12-28
forum: General Help
---

### Post by pgg1959 on 2010-12-28
I have been experiencing errors when trying to run Update Manager as well as Synaptic Pkg Mgr. This is the error it gives me:

Synaptic Package Manager:

E: Problem parsing dependency Depends
E: Error occurred while processing evince (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

W: Encountered status field in a non-version description

Update Manager:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'W:Encountered status field in a non-version description, E:Problem parsing dependency Depends, E:Error occurred while processing evince (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:The package lists or status file could not be parsed or opened.'


I run Lucid on an AMD64 system, Server edition. The system is running good otherwise. How can I fix this? 

My plan is to install VirtualBox 4.0 to run Windows7 inside Ubuntu.

---

### Post by Bucky Ball on 2010-12-28
You can't run both at once.

---

### Post by pgg1959 on 2010-12-28
> **Bucky Ball said:**
> You can't run both at once.

Ok, does this refer to Synaptic and Update Manager? I don't run both at the same time, just that the same error shows on both, as they are obviously connected.

If you are meaning VirtualBox and Windows7, that is something I can deal with later. I may not even run it on this box, am considering a whole different box, but I need to get the **Update Manager** problem solved first.

Any help is appreciated.

---

