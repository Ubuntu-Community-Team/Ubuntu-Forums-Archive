---
title: "'E:Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/user-ppa-na"
date: 2011-05-26
forum: General Help
---

### Post by nklnsk on 2011-05-26
have problem while trying to instal cinelerra:
 'E:Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/user-ppa-name-lucid.list, E:The list of sources could not be read.' 

Im on 10.4.

please help

---

### Post by plucky on 2011-05-26
> **nklnsk said:**
> have problem while trying to instal cinelerra:
 'E:Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/user-ppa-name-lucid.list, E:The list of sources could not be read.' 

Im on 10.4.

please help

Edit the file and remove the 'n' in line 2 with ```
gksudo gedit /etc/apt/sources.list.d/user-ppa-name-lucid.list
``` and if that doesn't work post the contents of the file.

Good Luck

---

### Post by nklnsk on 2011-05-26
Its working. I started update manager. Thanks

---

