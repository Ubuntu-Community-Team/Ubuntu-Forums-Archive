---
title: "Sharing Folders"
date: 2006-06-29
forum: General Help
---

### Post by _simon_ on 2006-06-29
I set up SAMBA the other day to share files with XP on a virtual machine.

At the time it also gave me the option of sharing files between just linux machines. How would I find this option again?

Also, how would I disable SAMBA as I have now finished with the virtual machine.

---

### Post by denkedran on 2006-06-29
to "unshare" a folder open a terminal and type
```
sudo shares-admin
```
there you can remove your shared directories from the list


to completly remove the sambaserver from your system
```
sudo apt-get remove --purge samba-common
```
or to disable it, uncheck samba from
```
sudo services-admin
```

---

### Post by _simon_ on 2006-06-29
thank you :)

---

