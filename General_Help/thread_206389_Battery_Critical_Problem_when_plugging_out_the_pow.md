---
title: "Battery Critical Problem when plugging out the power adapter"
date: 2006-06-30
forum: General Help
---

### Post by emperon on 2006-06-30
Hello , 
My problem is  when I plug out my laptop's  power adapter, even though the battery is fully charged, a baloon appears and telling me that my battery level is critical. And after few seconds it turns the power off.

I heard this was about a bug in Gnome Power manager. Is there a fix for this ?

---

### Post by ayoli on 2006-06-30
are you sure it's a bug og gnome power manager , does acpi works fine on your laptop ? try in a console:
```
ls /proc/acpi/battery/BAT0/
```

and if gnome-power-manager is the pb, you can desactivate itby removing it from session startup progs (menu System > preferences > sessions), then logout/login.
regards.

---

### Post by emperon on 2006-07-03
[QUOTE=ayoli]are you sure it's a bug og gnome power manager , does acpi works fine on your laptop ? try in a console:
```
ls /proc/acpi/battery/BAT0/
```

and if gnome-power-manager is the pb, you can desactivate itby removing it from session startup progs (menu System > preferences > sessions), then logout/login.
regards.[/QUOTE]

onorin@gandalf:~$ ls /proc/acpi/battery/C11F/
alarm  info   state
onorin@gandalf:~$ ls /proc/acpi/battery
C11F

I do not know if ACPI works or not. Now what ?

---

