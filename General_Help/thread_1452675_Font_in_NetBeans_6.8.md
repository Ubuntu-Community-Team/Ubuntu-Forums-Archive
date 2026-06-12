---
title: "Font in NetBeans 6.8"
date: 2010-04-12
forum: General Help
---

### Post by ReeRD on 2010-04-12
Is it possible to make the editor font in NetBeans look exactly the same as it does in Ubuntu 9.10's gnome terminal or gedit (that is, use the same font and make it antialiased)?

---

### Post by *Legion* on 2010-04-23
No. At least, not in the months I've been searching have I found a way.

Eclipse uses the SWT toolkit which supports native font rendering, including subpixel rendering.

Netbeans uses Swing, which doesn't.

Hence, I continue to use Eclipse and have never seriously evaluated Netbeans. I stare at text in my editor all day and I can't have it looking like crap, I'll go mad!

---

