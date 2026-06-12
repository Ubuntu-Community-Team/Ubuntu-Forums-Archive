---
title: "Booting Up Applications on Separate Display"
date: 2010-01-26
forum: General Help
---

### Post by sharpdust on 2010-01-26
When I login, I would like to have certain applications load up.
I can manage to get applications to load on my first monitor (0:0) very easily.

~./xinitrc

```
mrxvt &
mrxvt &
mrxvt &
mrxvt &
```

However, I want to be able to load up applications on the second display and the following:

```
setenv DISPLAY=beryllium:0.1 
opera &
```

doesn't seem to work. (beryllium is my hostname).

Does anybody have any suggestions or can point me to where (if any) error log files are generated from X11 startup.

Thank you.

---

