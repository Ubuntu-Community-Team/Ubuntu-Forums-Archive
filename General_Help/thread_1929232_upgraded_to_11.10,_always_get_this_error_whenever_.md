---
title: "upgraded to 11.10, always get this error whenever I execute ANY command in terminal"
date: 2012-02-21
forum: General Help
---

### Post by test_tube_baby on 2012-02-21
I get this error:

```
ERROR: ld.so: object '/usr/lib/libv4l/v4l2convert.so' from LD_PRELOAD cannot be preloaded: ignored.
```

whenever I type anything in the terminal and press enter.
Even with the ls command.

Even when I press tab as a shortcut to writing a path/file name.

Does anyone know a fix to this?

I recently upgraded to 11.10 and this has been troubling me since.

---

### Post by bluexrider on 2012-02-21
Something may be contained in the ~/.bashrc file. A quick look may tell you the reference.


```
 gksudo gedit ~/.bashrc
```

Take a look there. Remove the line that has that reference and save.

---

### Post by LinuxFan999 on 2012-02-21
Did you upgrade through the update manager?

If so, you will need to do a clean installation of Ubuntu 11.10.

Upgrading through the update manager is not recommended.

---

