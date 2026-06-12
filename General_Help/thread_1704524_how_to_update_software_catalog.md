---
title: "how to update software catalog?"
date: 2011-03-10
forum: General Help
---

### Post by naj690 on 2011-03-10
im trying to install microsoft fonts but the software centre said i need to update software catalog. how do i do that?

---

### Post by Frogs Hair on 2011-03-10
Accessories > Terminal  ```
sudo apt-get update
```

---

### Post by naj690 on 2011-03-11
are you sure that command update the SOFTWARE CATALOG and not just the system> coz i run the command and still cant install ms font

---

### Post by tredegar on 2011-03-11
System - Admin - Synaptic.
Settings - Repositories
Under "Ubuntu Software" Tab, enable "Proprietary Drivers (Restricted)
Close Software sources window.

Reload.

Now you will see **ubuntu-restricted-extras** listed, the MS fonts are part of that package, so select and install it.

---

### Post by naj690 on 2011-03-11
it worked. thx man

---

