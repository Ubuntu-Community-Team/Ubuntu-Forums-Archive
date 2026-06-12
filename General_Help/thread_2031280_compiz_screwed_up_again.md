---
title: "compiz screwed up again"
date: 2012-07-21
forum: General Help
---

### Post by icegood on 2012-07-21
Cannot run compiz, in particular unity1 doesn't work at all, and smth else. No terminal under <ctrl>+<alt>+T, no menus.
Log - cat /var/log/syslog | grep error:
```

Jul 21 02:04:16 ubuntu NetworkManager[1149]: <error> [1342825456.847299] [wifi-utils-nl80211.c:654] nl80211_wiphy_info_handler(): Don't know the meaning of NL80211_ATTR_CIPHER_SUITES 0x000fac06.
Jul 21 02:04:16 ubuntu NetworkManager[1149]: <error> [1342825456.891852] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth0): unable to read permanent MAC address (error 0)
Jul 21 02:04:48 ubuntu kernel: [   49.973463] compiz[1957]: segfault at 10 ip 00007fe346a382ac sp 00007fff53cd60e0 error 4 in libgtk-3.so.0.400.2[7fe346938000+47a000]
Jul 21 02:05:24 ubuntu NetworkManager[1149]: get_secret_flags: assertion `is_secret_prop (setting, secret_name, error)' failed 

```

---

### Post by daslinkard on 2012-07-28
Are you able to run terminal at all through the graphical user interface?

---

