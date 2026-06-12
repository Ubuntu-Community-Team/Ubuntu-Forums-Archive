---
title: "LibreOffice calc icon not showing up in the dock"
date: 2011-11-21
forum: General Help
---

### Post by hojjat on 2011-11-21
I didn't have this problem until today: When I open LibreOffice Calc from the Launcher, it's icon IS added to the dock, but when I open LibreOffice Calc by double clicking on a .ods file, it's icon IS NOT added to the dock, and I can't switch to its window using ALT+TAB. Also, if I maximize its window, I don't see the close/minimize/restore buttons on the shared title bar.

Same happens with LibreOffice Writer. The LibreOffice programs are the only ones affected.

---

### Post by lifeboy on 2011-11-21
Make a copy of ~/.libreoffice and then delete the original.  See if that fixes the problem.  If there are things that you need from your config in ~/.libreoffice, restore it and delete things selectively to determine which directory contains the problem component.

---

### Post by hojjat on 2011-11-21
I moved ~/.libreoffice to ~/.libreoffice-tmp and retried the above scenario. The problem persists.

---

### Post by vanadium on 2011-11-21
This is a problem of Unity. I see a "phantom" icon when I double click a document, which is better than having no icon at all. This only occurs to me when loading somewhat larger documents. Small documents that load fast correctly appear as a white mark next to the corresponding libreoffice icon.

Probably our different symptoms have the same cause. Sporadically, it also occurs to me that Unity "looses track" of the LibreOffice window, like you describe, but for me, it occurs rarely.

Here is a bug report:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/741995](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/741995)

---

