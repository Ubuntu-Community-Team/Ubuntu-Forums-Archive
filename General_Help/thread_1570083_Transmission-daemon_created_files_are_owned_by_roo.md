---
title: "Transmission-daemon created files are owned by root"
date: 2010-09-07
forum: General Help
---

### Post by toto56 on 2010-09-07
Hi everyone,

Did someone ever had problem with files ownership and transmission-daemon?

Every file created by transmission-daemon is owned by root.
When I pause a download and then restart it, I have a permission error.

If I do "ps -ef | grep trans", I see that transmission-daemon is run by user 104 (which is debian-transmission).

Does anyone know how to solve the ownership of created files problem?

Thanks,

---

