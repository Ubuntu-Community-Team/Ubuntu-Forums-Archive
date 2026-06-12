---
title: "Error anytime I try to install something."
date: 2010-07-09
forum: General Help
---

### Post by xVehemencityx on 2010-07-09
Hi.  Every time I try to install something, be it by the terminal, synaptic, or ubuntu software center, I get this error.

[code]
dpkg: parse error, in file '/var/lib/dpkg/available' near line 13789 package 'gnome-media':
 `Depends' field, invalid package name `libatk1.;-0': character `;' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
[\code]

---

### Post by Elfy on 2010-07-10
Try 

```
sudo dpkg --clear-avail && sudo apt-get update
```

---

