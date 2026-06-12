---
title: "jabref cannot open relative path linked pdf"
date: 2011-08-15
forum: General Help
---

### Post by ssj71 on 2011-08-15
Hello all, 
I'm using jabref for my thesis and the group has a shared network drive where we are storing all our pdfs and the .bib database. If I link the paper with an absolute path and set jabref's default directory I can open it through jabref. i.e.
smb://group@ourserver.usu.edu/group/mygroup/refs/94 brake dynamics effect on lane capacity, Maciuca.pdf

However others have linked their files through relative paths, i.e.
/mygroup/refs/94 brake dynamics effect on lane capacity, Maciuca.pdf

If I set jabref's default file directory to smb://group@ourserver.usu.edu/ then I can rename or move the those relative directory files through jabref, therefore it can find them but it cant open them in okular like it can in the first example above. I can also set the default directory to be relative to the .bib file with "." and the same result (can rename but not open). Also with home/me/.gvfs/group on ourserver.usu.edu same thing. Other directories when I try to rename the linked file it says file not found.

Anyone have a guess why? It seems the windows guys in the group aren't experiencing this.

Thanks

---

