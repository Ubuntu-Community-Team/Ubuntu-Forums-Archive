---
title: "Inactive windows transparent except Gimp image window?"
date: 2009-08-21
forum: General Help
---

### Post by gldearman on 2009-08-21
Hi, all,

I am using the Compiz Fusion ADD Helper plugin to make all inactive windows transparent.  For the most part, I really like the effect.

However, in one particular case, I would rather not have it.  In the Gimp, the image window and toolbox are different windows.  So, whenever I select the toolbox, the image I am working on becomes transparent and hard to see!

Does anyone know a way that I can make an exception so that the Gimp image window does not become transparent when inactive, but the rest of the windows continue to do so?

Thanks!

---

### Post by gldearman on 2009-08-21
OK, I solved this on my own.  I'll post the solution here in case anyone else ever needs it.

In CompizConfig Settings Manager, I went to the section on the ADD Helper plugin.  In the "Misc. Options" tab, there is a "Window Types" field.  Initially, it read:

```
Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal
```

I changed it to read:

```
(Toolbar | Utility | Dialog | ModalDialog | Fullscreen | Normal) & !title=GIMP$
```

This specifically excludes any window whose title ends in the letters "GIMP", like the GIMP Image Window.  Now, my transparency does not affect that window.

Thanks to everyone who read my post, even if they didn't know the answer!

---

