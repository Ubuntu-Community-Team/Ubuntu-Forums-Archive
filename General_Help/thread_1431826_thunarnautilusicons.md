---
title: "thunar/nautilus/icons"
date: 2010-03-17
forum: General Help
---

### Post by dzon65 on 2010-03-17
Hi.How can I adjust this.As shown in the screenshots,icons (folders) are different when Thunar's set as file manager instead of nautilus.

---

### Post by dzon65 on 2010-03-17
Perhaps this could work:

[LIST=1]
[*]in **/usr/share/applications/nautilus.desktop** to **Exec=thunar %U**
[*]in **/usr/share/applications/nautilus-folder-handler.desktop** to **Exec=thunar %U**
[*]in **/usr/share/applications/nautilus-home.desktop** to **Exec=thunar**
[/LIST]
Cause for now,I only changed the first exec-line.Anyone familiar with these settings?

---

