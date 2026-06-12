---
title: "Nautilus doesn't interpret &quot;~&quot; correctly"
date: 2010-10-12
forum: General Help
---

### Post by Oded on 2010-10-12
In past releases, entering the "~" operator in the location bar, nautilus would interpret it as "/home/$USER" but as of 10.10 I get an error saying:```

Could not find "/home/oded/.gnome2/nautilus-scripts/~/.gnome2".
```
I'm running nautilus-elementary but this behavior also occurred in the default nautilus app that shipped with 10.10

---

### Post by CompyTheInsane on 2010-10-13
Are you using Ubuntu 10.10? If so, I just found a bug report for this issue on Launchpad: [https://bugs.launchpad.net/nautilus/+bug/630512](https://bugs.launchpad.net/nautilus/+bug/630512)

It is still yet to be fixed. :(

---

### Post by WorMzy on 2010-10-13
It's an [upstream bug]("https://bugzilla.gnome.org/show_bug.cgi?id=628802").

---

