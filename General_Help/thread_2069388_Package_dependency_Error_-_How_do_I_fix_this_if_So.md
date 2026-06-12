---
title: "Package dependency Error - How do I fix this if Software center won't load?"
date: 2012-10-10
forum: General Help
---

### Post by pakennyusa on 2012-10-10
I been noticing my Ubuntu machine acting strange after I ran a Software Update. 

This is the error I get. I cannot launch the software center or force a uninstall of the file/package mentioned.

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_ferramroberto_java_ubuntu_dists_precise_main_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.'

Please advise.

---

### Post by iponeverything on 2012-10-10
try:

```
sudo mv /var/lib/apt/lists/ppa.launchpad.net_ferramroberto_java_ubuntu_dists_ precise_main_binary-amd64_Packages /root/
```

to just get the offending file out of the way..

---

