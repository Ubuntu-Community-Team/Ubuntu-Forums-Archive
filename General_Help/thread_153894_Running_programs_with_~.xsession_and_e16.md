---
title: "Running programs with ~/.xsession and e16"
date: 2006-04-02
forum: General Help
---

### Post by Fillepe on 2006-04-02
I'm trying to run gdesklets on login to e16. This should be able to be accomplished through~/.xsession. My one looks like this:

```

#!/bin/sh

gdesklets &

```

But when I login i get nothing and the following ~/.xsession-errors file is generated.

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "bepuzzled"
/etc/gdm/Xsession: Beginning session setup...

(gnome-terminal:8564): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(gnome-terminal:8564): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

```

Anybody got any ideas? gdesklets runs fine if I execute it myself from the command line. 

Thanks

---

