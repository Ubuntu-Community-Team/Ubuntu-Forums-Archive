---
title: "through openbox auto login?"
date: 2010-11-08
forum: General Help
---

### Post by KingMidas on 2010-11-08
How to setup Lubuntu through openbox auto login? :confused:

---

### Post by cavalier911 on 2010-11-08
[U]Works with Lubuntu 10.4 with LXDM display manager
[/U]
Add autologin=username to the first line of base in /etc/lxdm/default.conf

```
[base]
autologin=**your.username.here**
```

---

### Post by KingMidas on 2010-11-08
> **cavalier911 said:**
> [U]Works with Lubuntu 10.4 with LXDM display manager
[/U]
Add autologin=username to the first line of base in /etc/lxdm/default.conf

```
[base]
autologin=**your.username.here**
```

Thanks for Cavalier911 to reply. :P
Can I go directly to Openbox-Session Desktop instead of Lubuntu Desktop? I do not want to run rc.xml, but I want after logging in to auto run a specific program.

---

