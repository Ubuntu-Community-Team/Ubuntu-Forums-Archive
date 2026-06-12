---
title: "Only do automatic security updates"
date: 2010-12-10
forum: General Help
---

### Post by pieterberlijn on 2010-12-10
I'm trying to find a way to alter the repositories which Ubuntu auto-updates from. I know this is possible via the GUI (Software Sources -> Updates), but I want to find out what files dictate the behavior of auto-updates; i.e. I want to able to do it via command line.

---

### Post by karthick87 on 2010-12-10
```
sudo apt-get upgrade
```

---

### Post by searchfgold6789 on 2010-12-10
All the GUI does is edit your /etc/apt/sources.list, adding entries to the end of the file.'
There is a howto guide here:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by pieterberlijn on 2010-12-10
For clarification: if I remove other repositories from my sources file, I no longer can manually install packages from those specific repositories.

I want to alter which repositories are automatically updated from.

---

### Post by cherva on 2010-12-10
Maybe this will help...
[https://help.ubuntu.com/community/AutomaticSecurityUpdates]("https://help.ubuntu.com/community/AutomaticSecurityUpdates")

---

