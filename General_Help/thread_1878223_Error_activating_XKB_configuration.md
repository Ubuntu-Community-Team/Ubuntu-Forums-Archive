---
title: "Error activating XKB configuration"
date: 2011-11-09
forum: General Help
---

### Post by James4 on 2011-11-09
I use Persian layout for my keyboard and since some the characters are not in their right place I edit the keyboard layout using this file /usr/share/X11/xkb/symbols/ir.
It was always ok in previous versions of Ubuntu but in Oneiric I have been getting the error shown in the picture since I changed the layout.

[IMG]http://i.stack.imgur.com/XVvhp.png[/IMG]

these are also the results of the commands mentioned in the image:
the fist one:
```
_XKB_RULES_NAMES_BACKUP(STRING) = "evdev", "pc105", "us,ir", ",", "grp:alt_shift_toggle,grp_led:scroll"
_XKB_RULES_NAMES(STRING) = "evdev", "pc105", "us,ir", ",", "grp:alt_shift_toggle,grp_led:scroll"
```
second:

```
''
```

third:

```
@as []
```

and the last:

```
['grp\tgrp:sclk_toggle', 'lv3\tlv3:lalt_switch', 'grp_led\tgrp_led:scroll']
```

p.s. : I have attached my XKB configuration file just in case...

---

