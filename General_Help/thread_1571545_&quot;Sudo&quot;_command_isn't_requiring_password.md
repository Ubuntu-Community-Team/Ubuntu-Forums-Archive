---
title: "&quot;Sudo&quot; command isn't requiring password"
date: 2010-09-09
forum: General Help
---

### Post by Vistz on 2010-09-09
For some reason, whenever I enter a sudo command, it doesn't ask me for my password anymore. Is there a way I can fix this?

---

### Post by bodhi.zazen on 2010-09-09
Depends. After entering a password there is a 15 minute grace period.

```
sudo -k
``` will end that.

Otherwise you will need to look at your sudoers file

[http://www.sudo.ws/sudo/sudo.man.html](http://www.sudo.ws/sudo/sudo.man.html)

---

