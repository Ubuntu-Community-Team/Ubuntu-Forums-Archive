---
title: "You might want to run 'apt-get -f install' to correct these."
date: 2010-12-30
forum: General Help
---

### Post by ohlawd on 2010-12-30
```
The following packages have unmet dependencies:
 pidgin : Depends: pidgin-data (>= 1:2.7.9) but 1:2.7.7-1ubuntu0+pidgin1.10.10 is installed
E: Unmet dependencies. Try using -f.
```
And when I run -f install, I get the following:
```
Errors were encountered while processing:
 /var/cache/apt/archives/pidgin-data_1%3a2.7.9-1~getdeb1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What do I do? :(
I've tried deleting the package, etc. but nothing has worked so far

---

### Post by t4thfavor on 2010-12-30
```
 
sudo apt-cache clean
sudo apt-get update

```
Then try installing whatever it was you were trying.

---

### Post by ohlawd on 2010-12-30
```
ohlawd@ohlawd-desktop:/var/cache/apt/archives$ sudo apt-cache clean
E: Invalid operation clean
```
Apt-get clean didn't help either

---

### Post by bobcollard on 2010-12-30
Open Synaptic Package Manager and search for Pidgin, then, "Mark for Complete Removal"  Apply.
Next: reinstall pidgin.

---

