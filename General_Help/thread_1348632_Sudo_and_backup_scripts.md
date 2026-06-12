---
title: "Sudo and backup scripts"
date: 2009-12-07
forum: General Help
---

### Post by hashbangbinbash on 2009-12-07
I'm fairly sure it's been asked before but can't find it... how do you make a script that is to be carried out by crontab in your absence (such as a backup script) be run as sudo?

---

### Post by lloyd_b on 2009-12-07
> **hashbangbinbash said:**
> I'm fairly sure it's been asked before but can't find it... how do you make a script that is to be carried out by crontab in your absence (such as a backup script) be run as sudo?

The easiest way is to put the scripts in root's crontab, rather than your login's crontab:```
sudo crontab -e
``` to create/edit a root crontab.

Lloyd B.

---

### Post by hashbangbinbash on 2009-12-08
Of course! Thanks.

---

