---
title: "HOWTO: Having suspend/hibernate issues? Then try this..."
date: 2010-09-15
forum: General Help
---

### Post by Joshun on 2010-09-15
The suspend/hibernate features in ubuntu can have problems on some laptops. I have found this fixed it for me.

1) Open gconf editor (do alt-f2, type in gconf-editor and click ok).

2) Go to: Apps>Gnome Power Manager (click arrow to expand).

3) Click on 'Lock'.

4) Untick suspend and hibernate. This will disable the keyring lock on suspend and hibernate which may solve your problem:D.

---

