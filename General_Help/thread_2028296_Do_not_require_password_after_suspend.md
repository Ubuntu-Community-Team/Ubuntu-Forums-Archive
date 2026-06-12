---
title: "Do not require password after suspend"
date: 2012-07-17
forum: General Help
---

### Post by 98cwitr on 2012-07-17
Is there a way to not require a password when I am resuming after a suspend in 12.04?

---

### Post by boregard on 2012-07-18
yes, go to system settings then brightness &lock, then untick box that says require my password when waking from suspend.

---

### Post by 98cwitr on 2012-07-20
reopening this one...unchecking the box doesn't seem to work.

---

### Post by 98cwitr on 2012-07-26
bump....is there a bash command(s) for this?

---

### Post by 98cwitr on 2012-07-26
well now...seems like this worked :)

```
 gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```

---

