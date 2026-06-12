---
title: "online source for a quick look?"
date: 2009-10-13
forum: General Help
---

### Post by adaallen on 2009-10-13
I  need to take a quick look at ifconfig.c and was wondering if there is a quick way to inspect source code without having to download the whole repository.

---

### Post by lloyd_b on 2009-10-14
> **adaallen said:**
> I  need to take a quick look at ifconfig.c and was wondering if there is a quick way to inspect source code without having to download the whole repository.

A Google search turned up nothing like SourceForge's system of having the sources browseable, so I guess you're stuck fetching the sources from the repos.

Note that you don't have to download "the whole repository" - just the sources for the particular package.  In this case, "apt-get source net-tools" will create a directory with the sources for the net-tools package (which includes ifconfig.c).

Lloyd B.

---

