---
title: "Trouble creating a udev rule."
date: 2011-02-11
forum: General Help
---

### Post by Dnajun_Tnuieh on 2011-02-11
Trying to create udev rules for android phone but cannot create or edit udev files? :confused:

I'm using the latest Kubuntu by the way.

---

### Post by sisco311 on 2011-02-11
You have to create/edit the .rules file as root:
```
kdesudo kate /etc/udev/rules.d/50-android.rules
```

See: [uhelp]community/RootSudo[/uhelp]
and
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

### Post by Dnajun_Tnuieh on 2011-02-12
> **sisco311 said:**
> You have to create/edit the .rules file as root:
```
kdesudo kate /etc/udev/rules.d/50-android.rules
```See: [uhelp]community/RootSudo[/uhelp]
and
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

I figured it had something to do with that, I just didn't know how to get it. Thanks.

---

