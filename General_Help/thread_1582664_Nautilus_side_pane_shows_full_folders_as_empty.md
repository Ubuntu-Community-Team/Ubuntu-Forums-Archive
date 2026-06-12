---
title: "Nautilus side pane shows full folders as empty"
date: 2010-09-26
forum: General Help
---

### Post by SteelCore on 2010-09-26
When browsing my external hard disk I noticed that Nautilus' side pane marks directories that contain files as empty. Is this a bug or a misconfiguration on my part? Thanks

---

### Post by asmoore82 on 2010-09-26
By default, the Tree view ignores everything but subfolders.

You can change this in `gconf-editor` with the key "/apps/nautilus/sidebar_panels/tree/show_only_directories"

---

