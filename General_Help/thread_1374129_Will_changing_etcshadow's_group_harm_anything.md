---
title: "Will changing /etc/shadow's group harm anything?"
date: 2010-01-06
forum: General Help
---

### Post by Vunutus on 2010-01-06
I'm trying to set up the PHP PAM authentication module. It requires that apache be able to access the /etc/shadow file. The documentation for said module recommends changing the group on /etc/shadow as to allow apache to read it.

I notice on my ubuntu server 8.04 installation, the group on /etc/shadow is preset to "shadow". Is this for a reason? Can I safely chgrp it to www-data to allow my module to work?

---

### Post by Vunutus on 2010-01-06
bump

---

### Post by rnerwein on 2010-01-06
hi
i think you will have much fun if you change the permissions of /etc/shadow
:-(
ciao

---

### Post by cariboo on 2010-01-06
+1, leave it as it is, owner id should be root and group id should be shadow. If you change it, nothing may work.

---

### Post by Iowan on 2010-01-06
I'm not sure of the security ramifications (probably not good), but an alternative might be to add apache (www-data) to the shadow group.

---

