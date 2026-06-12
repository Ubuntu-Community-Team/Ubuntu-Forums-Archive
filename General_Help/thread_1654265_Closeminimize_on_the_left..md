---
title: "Close/minimize on the left."
date: 2010-12-28
forum: General Help
---

### Post by wavemaker on 2010-12-28
Gooday folks. I have had to ask this before. Can you point me in the right direction of changing these buttons back to the right hand side. Thanks in advance.

---

### Post by karthick87 on 2010-12-28
Type the following in terminal,
```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

---

### Post by wavemaker on 2010-12-29
Thanks mate. All good now.

---

### Post by karthick87 on 2010-12-29
You are welcome :) Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

