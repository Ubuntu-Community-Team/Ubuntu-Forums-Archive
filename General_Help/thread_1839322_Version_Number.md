---
title: "Version Number"
date: 2011-09-05
forum: General Help
---

### Post by neiljazz on 2011-09-05
How do you tell which version of Wubi you are using ?  Thanks, Neil

---

### Post by bcbc on 2011-09-05
Wubi.exe revisions are linked to specific Ubuntu releases. The release is shown on the top centre when installing Wubi. The revision is also shown (bottom left I think).

Rev 211 = Natty 11.04
Rev 197 = Maverick 10.10
Rev 192 = Lucid 10.04.3

This is just the "Windows installer" executable I am referring to. If you've already installed and want to know what release of Ubuntu you are running: 
```
cat /etc/lsb-release
```

---

