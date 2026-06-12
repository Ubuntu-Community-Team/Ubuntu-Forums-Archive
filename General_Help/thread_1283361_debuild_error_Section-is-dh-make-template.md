---
title: "debuild error: Section-is-dh-make-template"
date: 2009-10-05
forum: General Help
---

### Post by markseger on 2009-10-05
Anyone have any clue what this means at the end of my debuild run?  I can't find any references to 'template' in any of the files in my debian/ directory.
-mark

---

### Post by markseger on 2009-10-05
I finally figured this out.  Turned out in the 'install' section of the rules file I had left the make command commented out.  Personally I think this error message is horrible!  It doesn't tell me which file it's talking about or which line of that file is the problem.  Those 2 tiny pieces of information would have save me a LOT of time.  :(
-mark

---

