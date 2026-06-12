---
title: "Latex beamer :"
date: 2011-11-15
forum: General Help
---

### Post by waqawaqa on 2011-11-15
A code of Latex in Beamer, which was running perfectly fine in Windows 7, using Winedt and miktex. 
But the same code on Ubuntu giving the error:
```

[PDFLatex]Finished with exit code 1
./Sample.tex:5:File 'stmaryrd.sty' not found. \usepackage
[PDFLatex] 1 error, 0 warnings, 0badboxes
```

I tried to include that sty file inside the folder, but it again asking for another sty file.. this chain goes till 3 step further, then I got message like xy.sty is not found. I added that.. now getting error: 
```
No input file like xy-error something like that
```

So I got the original running code of the same. Isn't it possible that I get the Kile+ latex environment on Ubuntu as if I don't get any error with this code, which was perfectly running on Windows 7.

---

### Post by Chronon on 2011-11-15
A quick search suggests that it's part of texlive-math-extra, so try installing that package and recompile your document.

---

