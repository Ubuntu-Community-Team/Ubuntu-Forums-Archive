---
title: "Firefox LP PPA Update Error"
date: 2010-04-07
forum: General Help
---

### Post by RazzyDaz on 2010-04-07
The software updating icon is showing that there are updates for firefox. However, when I go to update them, I receive this error:


W: Failed to fetch [http://ppa.launchpad.net/ubuntu-mozi...armic_i386.deb](http://ppa.launchpad.net/ubuntu-mozi...armic_i386.deb)
404 Not Found


Anyone know how to fix this problem?

Thanks!

---

### Post by lidex on 2010-04-07
How did you install this ppa and what is the actual name?

---

### Post by lovinglinux on 2010-04-07
Open "System >> administration >> Software Sources >> Other Software", then delete the ppa giving problems, then add this:

```
ppa:ubuntu-mozilla-daily/ppa
```

---

