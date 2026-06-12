---
title: "PDF document became damaged"
date: 2011-07-25
forum: General Help
---

### Post by imaginaryfruit on 2011-07-25
I tried to open a pdf document and got the message "PDF document is damaged". I was able to open this document a few months ago (before upgrading from 10.10 to 11.04; this is the first time I've tried since upgrading). 

I also tried recompiling the tex file (I'm using lualatex) but got errors that definitely weren't present last time I compiled it (again, before I upgraded). 

Any ideas what might have happened, and how I might fix it? 

Thanks!

---

### Post by mikejonesey on 2011-07-25
don't think it's fixable... but try opening it with different apps, especially the native adobe reader rather than docment viewer... as a last resort you can attempt to convert to html with pdftohtml or the online tool on adobe's website...

---

### Post by imaginaryfruit on 2011-07-25
Thanks for your quick reply!

No joy with adobe or with any others. The only error message containing information came from xpdf:

```
Error: Couldn't find included config file: '/usr/share/xpdf/arabic' (/etc/xpdf/includes:6)
Error: Couldn't find included config file: '/usr/share/xpdf/cyrillic' (/etc/xpdf/includes:7)
Error: Couldn't find included config file: '/usr/share/xpdf/greek' (/etc/xpdf/includes:8)
Error: Couldn't find included config file: '/usr/share/xpdf/hebrew' (/etc/xpdf/includes:9)
Error: Couldn't find included config file: '/usr/share/xpdf/latin2' (/etc/xpdf/includes:10)
Error: Couldn't find included config file: '/usr/share/xpdf/thai' (/etc/xpdf/includes:11)
Error: Couldn't find included config file: '/usr/share/xpdf/turkish' (/etc/xpdf/includes:12)
***** MediaBox = ll:0,0 ur:595.276,841.89
***** CropBox = ll:0,0 ur:595.276,841.89
***** Rotate = 0
Segmentation fault
```

Does this help me at all or is it a lost cause?

I'm more concerned about the .tex file not compiling properly any more. Anyone know why lualatex might suddenly have errors it didn't last time I compiled?

Thanks!

---

