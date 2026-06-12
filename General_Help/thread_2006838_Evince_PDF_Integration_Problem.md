---
title: "Evince PDF Integration Problem"
date: 2012-06-19
forum: General Help
---

### Post by rei12 on 2012-06-19
When trying to integrate Evince into web browsers, I got an inconsistent behaviour. The integration appeared to be working, but sometimes PDF documents were still opened separately (outside web browsers). I had the same result in Firefox 13 and Opera 12.

Operating System: Ubuntu 12.04 (64 bit)
- Evince 3.4
- Mozplugger 1.14.3
- Mozplugger configuration:
application/pdf: pdf: PDF file
application/x-pdf: pdf: PDF file
text/pdf: pdf: PDF file
text/x-pdf: pdf: PDF file
        repeat noisy swallow(evince) fill: evince "$file"
        repeat swallow(acrobatreader) fill: acroread -geometry +9000+9000 +useFrontEndProgram -tempFileTitle acrobatreader "$file"
        repeat noisy swallow(win) fill: xpdf -g +9000+9000 "$file"
        repeat noisy swallow(gv) fill: gv -safer -quiet -antialias -geometry +9000+9000 "$file"

Is there a way to prevent this inconsistency?

---

