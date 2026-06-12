---
title: "need a small script."
date: 2011-10-17
forum: General Help
---

### Post by SE7EN-LOCSTA on 2011-10-17
my laptop's screen does not turn back on after resume from suspend/dim. the only thing i know that fixes it is the command "sudo setpci -s 00:02.0 F4.B=00" - it won't let me access some file in /sys/ without sudo. i tried making that a keyboard shortcut, but it didnt do anything. being an admin task, do i have to run it in a terminal so i can give password, or is there a script or something i could run that would type the command for me?

---

### Post by gsmanners on 2011-10-17
How about:

```
gksudo setpci -s 00:02.0 F4.B=00
```

That way, you can run it sans terminal.

---

### Post by SE7EN-LOCSTA on 2011-10-17
thank you much

---

