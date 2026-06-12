---
title: "Dependency problems."
date: 2009-10-11
forum: General Help
---

### Post by BUSHYBOB on 2009-10-11
"Package linux-image-2.6.24-24-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-24-generic (--configure):
 dependency problems - leaving unconfigured"

How can I find what dependency is missing or corrupt?

---

### Post by BUSHYBOB on 2009-10-17
bump

---

### Post by oldos2er on 2009-10-17
Which version of Ubuntu are you running? Have you checked to make sure all repositories are enabled?

---

### Post by synapsys on 2009-10-17
Maybe try this, substituting packagename of course.

```
sudo apt-get build-dep packagename
```

---

### Post by slakkie on 2009-10-17
> **oldos2er said:**
> Which version of Ubuntu are you running? Have you checked to make sure all repositories are enabled?

Kernel 2.6.24 is 8.04 aka Hardy.

Could you run a aptitude install -s linux-image-generic? 

apt-cache depends, aptitude why, and aptitude show will help you determine which dependencies a package has. You could also, but you need to be running on a different kernel, remove the 24-24 kernel and reinstall it.

---

