---
title: "Epiphany browser"
date: 2005-01-24
forum: General Help
---

### Post by ctt1wbw on 2005-01-24
Is there any way to disable the underlining of links in the Epiphany web browser?  It's really kind of annoying.  I know how to do it in other browsers...

---

### Post by martijntje on 2005-01-24
If i'm not mistaken, epiphany is based on the gecko engine, right?

In the directory where you installed epiphany, there should be a folder called chrome, somewhere in that folder, there should be a file caled user.css, or something like that. You probably get the point: find the point where it says 'a:hover' and add a line to that section called 'font-decoration: none;'

If you don't want websites to override this behaviour, you may end the line with !important.

---

