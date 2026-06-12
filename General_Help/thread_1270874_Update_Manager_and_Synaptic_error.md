---
title: "Update Manager and Synaptic error"
date: 2009-09-20
forum: General Help
---

### Post by sumone on 2009-09-20
Hi All

After installing Opera 10 I got the following message when Update Manager ran:

An unresolvable problem occurred while initialising the package information.

Please report this bug for the 'update-manager' package and try to include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

Running Synaptic produces the same error, is there any terminal commands i can use to resolve this?

Thanks in advance

---

### Post by cogier on 2009-09-20
Try running the following in Terminal. If it's a package problem this may fix it.
```
sudo apt-get install -f
```

---

