---
title: "Automatic Updates"
date: 2011-08-17
forum: General Help
---

### Post by beradero on 2011-08-17
[FONT=Arial]Hello,
I am reading the section about "Package Management > Automatic Updates" in the server documentation, and I have one question about /etc/apt/apt.conf.d/10periodic.

What is the diff between these two options[FONT=Verdana]?[/FONT]
[/FONT]```

APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::Unattended-Upgrade "1";

```

---

### Post by beradero on 2011-08-17
Huumm.. I think
```
APT::Periodic::Download-Upgradeable-Packages "1" -> Only downloads the packages.
APT::Periodic::Unattended-Upgrade "1" -> After the package is downloaded, install it.
```

Is it?

---

### Post by CatKiller on 2011-08-17
That's how I'd read it, too.

---

