---
title: "apt-get question"
date: 2011-01-22
forum: General Help
---

### Post by Wtower on 2011-01-22
I'm a bit confused with this: When I log on a server it says 6 packages can be upgraded. When I run apt-get upgrade though it says that 0 upgraded, 0 new installed, 0 uninstalled and 3 cannot be upgraded. Occasionaly, when there are indeed more updates available than those 6 packages, upgrade works fine. I believe the server is up-to-date. Why is that?

---

### Post by plucky on 2011-01-22
> **Wtower said:**
> I'm a bit confused with this: When I log on a server it says 6 packages can be upgraded. When I run apt-get upgrade though it says that 0 upgraded, 0 new installed, 0 uninstalled and 3 cannot be upgraded. Occasionaly, when there are indeed more updates available than those 6 packages, upgrade works fine. I believe the server is up-to-date. Why is that?

Usually it is a dependency problem and it has to wait until the correct,up-to-date packages are available before it will install.

Could be the server you are downloading from is out of step with the Main Server due to time differences.

Good Luck

---

### Post by Wtower on 2011-01-22
Ok. Nothing too serious then and nothing I have done :)
Cheers

---

