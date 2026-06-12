---
title: "$ sudo COMMAND and # COMMAND have different results"
date: 2012-09-20
forum: General Help
---

### Post by sombrancelha on 2012-09-20
Hello,

When I ran
```

$ sudo echo -n 50 > /sys/class/backlight/acpi_video0/brightness

```
I got permission denied. However, if I ran
```

$ sudo su
# echo -n 50 > /sys/class/backlight/acpi_video0/brightness

```

it worked. Why?

---

### Post by CharlesA on 2012-09-20
you cannot use redirects with sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

```
echo -n 50 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

---

### Post by sombrancelha on 2012-09-20
Thanks!

---

