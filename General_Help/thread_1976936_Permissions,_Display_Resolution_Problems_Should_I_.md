---
title: "Permissions, Display Resolution Problems: Should I Create a New xorg.conf file?"
date: 2012-05-09
forum: General Help
---

### Post by mulluysavage on 2012-05-09
I've been having some problems accessing folders- I don't seem to be the owner of the root folder, for instance, even though I'm the administrator. Also having problems accessing other files.

And then today I turn on my computer and get a 4:3 resolution instead of the usual 16:9. When I run my nvidia-xconfig, I get:


Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.


ERROR: Unable to write to directory '/etc/X11'.

I see stuff in forums about this, but I'm wondering if all these problems are related and my xorg.conf file is getting messed up, and I should start a fresh one or something. But I can't access it, because I don't have permission...what to do?

---

### Post by bogan on 2012-05-10
Hi!, [B]mulluysavage,
[/B]
Have you tried```
 gksudo nautilus /etc/X11/
``` Then edit, rename, or delete xorg.conf.

Or use gedit, or another editor, directly instead of 'nautilus' in that command. ie:```
gksudo gedit /etc/X11/xorg.conf
```

Do not forget to Save after editing!

Chao!, **bogan**.

---

