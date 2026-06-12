---
title: "Difference between purge, dpkg -r, remove"
date: 2009-09-29
forum: General Help
---

### Post by arnab_das on 2009-09-29
whats the difference between the following commands?

1. sudo apt-get purge <package>

2. sudo dpkg -r <package>

3. sudo apt-get remove <package>

---

### Post by *malagant* on 2009-09-29
Afaik:
sudo apt-get purge <package> removes **all** files, including config files etc.

apt-get is just a frontend for dpkg, so 2) and 3) should do the same

---

### Post by diesch on 2009-09-29
If there are package installed which depend on the package you want to remove, dpkg -r gives you an error while apt-get offers to remove the depending packages.

---

### Post by arrange on 2009-09-29
> ***malagant* said:**
> Afaik:
sudo apt-get purge <package> removes **all** files, including config files etc.

Does NOT remove the corresponding */var/cache/apt/archives/*.deb* file and config files in your */home* directory though.

---

