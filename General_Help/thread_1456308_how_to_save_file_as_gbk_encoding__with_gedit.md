---
title: "how to save file as gbk encoding  with gedit?"
date: 2010-04-17
forum: General Help
---

### Post by luofeiyu on 2010-04-17
i want to save my file as gbk encoding with gedit,gedit can't do it,please see the attachment,what's wrong?

---

### Post by byStanderone on 2010-04-17
...$> gconf-editor
it will open configuration editor, and choose /apps/gedit-2/preferences/encoding, edit "auto_detected" key, add "GBK" before "ISO-8859-15"

---

