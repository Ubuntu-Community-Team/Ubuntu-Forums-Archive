---
title: "Applications start seemingly at random on login"
date: 2012-04-21
forum: General Help
---

### Post by J V on 2012-04-21
XFCE seems to be saving my session on logout, but the option is unchecked.

Skype, Mangler and Firefox are often started when I log in, but thunderbird never is.

Any way to track this problem down?

---

### Post by brainwash on 2012-04-21
Delete the saved session data, so it won't be used on next start:
```
rm -r ~/.cache/sessions/
```

---

### Post by J V on 2012-04-21
Great! Now I know which folder it's in ^^

---

