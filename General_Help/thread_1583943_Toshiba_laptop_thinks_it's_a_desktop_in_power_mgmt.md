---
title: "Toshiba laptop thinks it's a desktop in power mgmt."
date: 2010-09-28
forum: General Help
---

### Post by 98174 on 2010-09-28
I have a Toshiba Satellite, and the battery icon is always charging, regardless of whether or not the battery is in there or it's completely full.

```

admin@HP01:~$ cat /proc/acpi/battery/BAT0/info
cat: /proc/acpi/battery/BAT0/info: No such file or directory
admin@HP01:~$ cat /proc/acpi/battery/BAT1/info
present:                 no

```

It seems like the laptop is not even aware that there's a battery slot?  Any ideas on how to fix this?  Frustrating to be working on battery power and having it completely turn off with no warning.

---

