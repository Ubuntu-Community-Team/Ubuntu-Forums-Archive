---
title: "Mozplugger not swallowing Evince"
date: 2011-12-15
forum: General Help
---

### Post by aetherius0 on 2011-12-15
I thought I had configured mozplugger correctly with the following:

```
application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
application/x-postscript:ps:PostScript file
application/postscript:ps:PostScript file
    repeat noisy swallow(evince) fill: evince "$file"
```However, a new window of Evince still opens with the PDF. Interestingly, the tab in Firefox has the address to the PDF but displays nothing. Any suggestions?

---

