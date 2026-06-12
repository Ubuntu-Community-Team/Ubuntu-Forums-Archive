---
title: "grep  can't  search  pdf  file?"
date: 2010-06-02
forum: General Help
---

### Post by luofeiyu on 2010-06-02
i want to search some key words in some pdf files
grep  myword  ~/test.pdf
that command can't work!
 grep  command  can't search pdf  file??

---

### Post by kaibob on 2010-06-02
> **luofeiyu said:**
> i want to search some key words in some pdf files
grep  myword  ~/test.pdf
that command can't work!
 grep  command  can't search pdf  file??

I don't believe grep will search a PDF file. One alternative is to use the pdftotext utility:

```
pdftotext test.pdf - | grep myword
```

It is often best to use the pdftotext -layout option.

The above command will only work with PDF files that contain readable text. Some PDF files--including most scanned documents--do not contain readable text.

---

