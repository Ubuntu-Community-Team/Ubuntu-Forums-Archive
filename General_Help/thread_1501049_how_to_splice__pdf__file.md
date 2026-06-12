---
title: "how to splice  pdf  file?"
date: 2010-06-03
forum: General Help
---

### Post by luofeiyu on 2010-06-03
i use the command:
  cat  ~/test/001.PDF    >> ~/test/total.pdf
  cat  ~/test/002.PDF    >> ~/test/total.pdf
what i want to get is  total.pdf  which contains  ~/test/001.PDF and ~/test/002.PDF,in fact there is only ~/test/002.PDF  in   total.pdf ,no   ~/test/001.PDF,how can i do?

---

### Post by kaibob on 2010-06-03
> **luofeiyu said:**
> i use the command:
  cat  ~/test/001.PDF    >> ~/test/total.pdf
  cat  ~/test/002.PDF    >> ~/test/total.pdf
what i want to get is  total.pdf  which contains  ~/test/001.PDF and ~/test/002.PDF,in fact there is only ~/test/002.PDF  in   total.pdf ,no   ~/test/001.PDF,how can i do?

The commandline utilities, Ghostscript and PDFtk, will do what you want.

```
gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -sOutputFile=[output file] [input files]
```

or

```
pdftk [input files] cat output [output file]
```

In the above commands, you need to insert the names of the input and output files. When combining a large number of PDF files, it may be easiest to place them in an empty directory and use *.pdf as the input files.

---

