---
title: "alt+click ubuntu 11.10"
date: 2012-02-24
forum: General Help
---

### Post by dragonryu on 2012-02-24
How to disable alt+click to move a window in ubuntu 11.10?

---

### Post by dragonryu on 2012-02-24
This worked for me:

```
gconftool-2 --set /apps/metacity/general/mouse_button_modifier --type string '<SUPER>'
```it switchs to <SUPER> + click, instead of alt+click

---

