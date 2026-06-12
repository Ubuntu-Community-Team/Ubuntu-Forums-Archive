---
title: "Problem with Update Manager"
date: 2012-02-11
forum: General Help
---

### Post by Selwonk13 on 2012-02-11
For about 3 days now, I have been getting this message when I try to start the 'Update Manager".

E: Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dist_natty_security_binary-i386_Packages, E: The package lists or status file could note be parsed or opened.
 
Does anyone know a command to fix this. Thank you.

---

### Post by mikewhatever on 2012-02-11
Try this:
```

sudo rm /var/lib/apt/lists/security.ubuntu.com_ubuntu_dist_natty_security_binary-i386_Packages

sudo apt-get update

```

The update manager should work afterwards.

---

