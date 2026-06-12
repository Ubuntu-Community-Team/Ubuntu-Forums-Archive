---
title: "Samba permissions problem"
date: 2009-09-07
forum: General Help
---

### Post by Skerit on 2009-09-07
Hi everyone,

I used to run a debian server, where everything worked as expected. However, now I'm running Ubuntu 9.04 at the backend (with the same samba configuration files) and I'm running into a few problems.

There are certain files on the server that belong to user A, but the "users" group also has complete access to it.

When user B, also in the "users" group, tries to modify these files on the server it works without a problem.

When I mount the directory as user B, using samba, it does NOT work. I do not have sufficient permission.

Can anyone tell me where I'm going wrong?

---

