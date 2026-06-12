---
title: "XP drive letter followed by $"
date: 2010-01-18
forum: General Help
---

### Post by tsucol11 on 2010-01-18
I am presently using Ubuntu 9.10 on 1 system and XP pro on a second computer. While connecting to windows from ubuntu I see the shared folders plus a bunch of folders/drives such as E$, F$, G$ etc. I cannot open these folders.

What do the folders ending in $ represent?

Thank you.

Brian

---

### Post by eriqjaffe on 2010-01-18
Those are "administrative" shares, which are set by the system and hidden from view when people browse on the network - at least when they browse through Windows.  They can only be accessed by people with administrative privileges on the PC, so if you want to get to them, you may have to connect with alternate credentials.

As the share names imply, they are the root level of your hard drive(s):  C$ is the administrative share for C:, and so forth.

---

### Post by tsucol11 on 2010-01-19
> **eriqjaffe said:**
> Those are "administrative" shares, which are set by the system and hidden from view when people browse on the network - at least when they browse through Windows.  They can only be accessed by people with administrative privileges on the PC, so if you want to get to them, you may have to connect with alternate credentials.

As the share names imply, they are the root level of your hard drive(s):  C$ is the administrative share for C:, and so forth.

thank you

brian

---

