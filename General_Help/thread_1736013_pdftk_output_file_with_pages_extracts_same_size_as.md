---
title: "pdftk output file with pages extracts same size as input file"
date: 2011-04-22
forum: General Help
---

### Post by thaitang on 2011-04-22
I am curious if perhaps I am doing something wrong extracting pages from a pdf doc using pdftk and creating a new file. I am only extracting the odd pages from the file and outputting them to a new file that is now only 20 pages instead of the input's 40 pages, yet the new output file is still 1.4Mb in size, the same as the original.

It seems strange to extract only half the pages of a large document and end up with a result that is the same size. Does anyone have any suggestions or advice how to streamline the resulting pdf's using pdftk?

BTW this is the command I am using, in case perhaps I am missing an option to optimize file size or something:

```
pdftk A=ch15.pdf cat A1-40odd output odd.pdf
```

cheers,
tt

---

### Post by dingodog on 2011-04-23
This usually happens with pdftk and certain pdf files. Probably, the problem is related to XREF table of pdf and to pdftk both

try with Split tool from

***multivalent***
- [http://goo.gl/QGgvb](http://goo.gl/QGgvb) (latest free version with tools)

```
java -cp path...to..Multivalent.jar tool.pdf.Split -page odd file.pdf
```

---

