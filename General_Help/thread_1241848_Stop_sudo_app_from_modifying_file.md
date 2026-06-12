---
title: "Stop sudo app from modifying file"
date: 2009-08-16
forum: General Help
---

### Post by kRiSiS112 on 2009-08-16
Hey, all.  I have a purely hypothetical question.

I have a file that I don't want modified, and an app I need to run.

This app requires sudo privileges for a lot of actions, one of them being to modify this file.  Is there any way to protect it from being changed during the process of running this app?

Thanks for your insight!

EDIT: Oh, and I don't have the source code to the app, so I can't modify its behavior.

---

### Post by Bachstelze on 2009-08-16
You could use AppArmor.

---

