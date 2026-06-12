---
title: "GDebi ignores system themes ?!"
date: 2009-07-01
forum: General Help
---

### Post by yesint on 2009-07-01
Dear All,
I've noticed strange behavior of GDebi package installer. When I change the system theme it ignores new theme and is shown in ugly default gnome theme (a-la GTK 1.0). Any ideas how to fix this?

---

### Post by Legace on 2009-07-01
Type following in Terminal, then open GDebi and see if it worked.
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

---

### Post by yesint on 2009-07-02
> **Legace said:**
> Type following in Terminal, then open GDebi and see if it worked.
```
sudo ln -s ~/.themes /root/.themes
sudo ln -s ~/.icons /root/.icons
sudo ln -s ~/.fonts /root/.fonts
```

Thanks! This seems to work.

---

