---
title: "latex help"
date: 2010-09-06
forum: General Help
---

### Post by ddmn on 2010-09-06
hi guys,

i'm using a two column in latex, when trying to insert my figure in single column it doesn't appear. but when i insert it spanning both columns it works fine.

any idea on how can i insert my figure in a single column?

i'm using kile in kde.

---

### Post by afrowildo on 2010-09-06
Try setting it to half text width like so:

```
\includegraphics[width=0.5\textwidth]{FIGURE_NAME}
```

---

### Post by ddmn on 2010-09-06
> **afrowildo said:**
> Try setting it to half text width like so:

```
\includegraphics[width=0.5\textwidth]{FIGURE_NAME}
```


i've tried this one and it doesn't seem to work out. what maybe the problem now?

---

