---
title: "Automatically generate pdf files from Spreadsheet worksheets"
date: 2009-11-16
forum: General Help
---

### Post by g.a. on 2009-11-16
Hi,

I have the following problem:

I have a spreadsheet file (OpenOffice or Excel) containing 50 Worksheets. For each of them I need to create a proper pdf file and I would like to automate the procedure.

One solution might be to find a macro/tool procedure to do it under OpenOffice but I have not found it.

As an alternative I might create manually a single pdf file where each page corresponds to a worksheet. From it is there any tool to split it in single files each containing one page ?

As the alternative of the alternative I might extract an html file from the original Spreadsheet file. Any hint?

Thanks in advance,
g.

---

### Post by kaibob on 2009-11-16
> **g.a. said:**
> As an alternative I might create manually a single pdf file where each page corresponds to a worksheet. From it is there any tool to split it in single files each containing one page ?

The pdftk command-line utility (which is in the repo's) will split an existing pdf file into individual pages:

```
pdftk input.pdf burst
```

[http://www.accesspdf.com/pdftk/](http://www.accesspdf.com/pdftk/)

Ghostscript will do the same thing but requires a shell script.

---

### Post by g.a. on 2009-11-17
this one (pdftk) works perfectly. thanks.

g.

---

