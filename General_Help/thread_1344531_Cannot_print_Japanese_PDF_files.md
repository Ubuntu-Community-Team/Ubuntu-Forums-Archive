---
title: "Cannot print Japanese PDF files"
date: 2009-12-03
forum: General Help
---

### Post by ToshibaLaptoplinux on 2009-12-03
I have never been able to print Japanese Language PDF files and it has now become a critical issue for me.

First let me state that this is a problem only with PDF's. ANy other Japanese language document (ie: odt, doc, txt, xls, etc) renders properly to screen and prints properly.

I have Document Viewer, Adobe 9.2, and XPDF Japanese installed on Jaunty 9.04

Document Viewer:
Expected Behavior: Open Japanese PDF, render characters correctly to screen, and print characters correctly to hard copy.
What Happens: PDF will open. ONLY roman characters render to screen. There is no gobbledygook. Places where Japanese characters are present are just left blank. Printing exhibits the same behavior.

XPDF-Japanese:
Expected Behavior: Open Japanese PDF, render characters correctly to screen, and print characters correctly to hard copy.
What Happens: Document will render correctly to screen. Japanese characters and Roman characters BUT when printing Japanese characters print as gobbledygook and Roman characters print correctly.

Adobe Reader 9 with Acroasianfont pack installed:
Expected Behavior: Open Japanese PDF, render characters correctly to screen, and print characters correctly to hard copy.
What Happens: Document neither renders correctly to screen nor prints correctly to hard copy.
Adobe throws the following errors; "Rebuilding:This file is damaged but being repaired" and then "The Japanese Language support pack is required to display this page properly..."
These errors are interesting because  1) The support pack is installed and 2) They occur with ALL Japanese language PDF's. Note: All Japanese PDF's render to screen and print properly on a Japanese Windows OS machine and an English Windows OS machine.

This is a problem regardless of the printer used. Any ideas?

---

### Post by rmcd on 2009-12-11
Have you installed the package poppler-data? This fixed the problem for me.

Unbelievable that this isn't installed by default.

---

### Post by jezebel on 2010-02-22
Yep - installing the poppler-data package totally fixed the problem for me too.

Just go to the Synaptic Package Manager and do a search for 'poppler-data'. Then install and you should be good to go.

---

### Post by Kleenux on 2010-05-11
> **rmcd said:**
> Have you installed the package poppler-data? This fixed the problem for me.

For me too, thanks!

> **rmcd said:**
> Unbelievable that this isn't installed by default

Unbelievable, indeed.

---

### Post by ToshibaLaptoplinux on 2011-09-05
Ugh! I can swear I marked this as solved and indicated that your suggestion fixed the problem but am doing so again in the event someone with the same issue searches for a solution. to the same problem. Thanks.

---

