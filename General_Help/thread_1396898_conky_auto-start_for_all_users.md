---
title: "conky auto-start for all users???"
date: 2010-02-02
forum: General Help
---

### Post by eufran on 2010-02-02
Hello

I have a S.O. integrated with a LDAP Domain, and i like to auto-start my conky.conf for all users can be login session on this PC.

Now i write a script autostart.sh, and i move into /etc/profile.d/autostart.sh.

This script only have one line like:
#!/bin/bash
conky;
exit;


The conky auto-start for all users but the gnome not continue starting....

where can i put this script or other change to do it?'

Sorry for my english, im spanish.

---

### Post by Barriehie on 2010-02-02
> **eufran said:**
> Hello

I have a S.O. integrated with a LDAP Domain, and i like to auto-start my conky.conf for all users can be login session on this PC.

Now i write a script autostart.sh, and i move into /etc/profile.d/autostart.sh.

This script only have one line like:
#!/bin/bash
conky;
exit;


The conky auto-start for all users but the gnome not continue starting....

where can i put this script or other change to do it?'

Sorry for my english, im spanish.

I would try:
```

conky &

```

---

### Post by eufran on 2010-02-03
I try with this code coky &; but dont work. 

Help please

---

### Post by Barriehie on 2010-02-03
Put:
```

conky &

```
at the end of **/etc/profile**

---

