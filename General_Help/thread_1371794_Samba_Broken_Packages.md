---
title: "Samba Broken Packages"
date: 2010-01-03
forum: General Help
---

### Post by Mystery Smith on 2010-01-03
Hi everyone,

I'm trying to get file sharing working and every time I try to share a file it tries to install the program and then I get an error. I assumed it was a problem with Samba so I tried to install it myself but it says that there are "Unmet Dependencies" and that there is a "Broken package." Can anyone please help?

Thanks,
Tim

---

### Post by zvacet on 2010-01-04
System>admin>software sources>check all under Ubuntu software and first two under updates tab.Reload.In applications>accessories>terminal type

```
sudo apt-get -f install
```

---

