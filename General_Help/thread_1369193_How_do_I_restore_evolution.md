---
title: "How do I restore evolution?"
date: 2009-12-31
forum: General Help
---

### Post by mojo_man on 2009-12-31
Hello,

My task bar ( the bar on top that has APPLICATIONS, PLACES, SYSTEM) disappeared) so I renamed .gconf and .gconfd to .gconf_old and .gconfd_old and the files were restored so I got the bar back. When I start evolution though it asks me to reset up my account--it does not use the old config settings.

Nothing is erased it seems. I just need to direct Evolution to the old files it seems. HOw can I do this please?

Mohit

---

### Post by oldos2er on 2009-12-31
Run mkdir ~/.gconf/apps/evolution, then copy ~/.gconf_old/apps/evolution/* to ~/.gconf/apps/evolution/

---

