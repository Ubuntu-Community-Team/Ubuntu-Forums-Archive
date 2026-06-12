---
title: "Update to 9.10 breaks pdftk (or itext, or java)"
date: 2009-11-02
forum: General Help
---

### Post by david.mihola on 2009-11-02
Hello,

I hope this is the correct forum for this question - if not, please direct me to the correct one!

I just finished the update to 9.10 and tried to use pdftk again, but this is what happens:

pdftk page1.pdf page2.pdf cat output both_pages.pdf
Unhandled Java Exception:
java.lang.ArrayIndexOutOfBoundsException: 10
   at java.text.SimpleDateFormat.formatWithAttribute(libgcj.so.10)
   at java.text.SimpleDateFormat.format(libgcj.so.10)
   at java.text.DateFormat.format(libgcj.so.10)
   at com.lowagie.text.Document.addCreationDate(itext-2.1.5.jar.so)
   at com.lowagie.text.pdf.PdfDocument.<init>(itext-2.1.5.jar.so)
   at com.lowagie.text.pdf.PdfCopy.<init>(itext-2.1.5.jar.so)

pdftk is version 1.41+dfsg-1
libitext-java and libitext-java-gcj are both version 2.1.5-1ubuntu2
libgcj10 is version 4.4.1-5ubuntu2

and the problems happens with both
java-6-sun (build 1.6.0_16-b01)
and 
java-6-openjdk (6b16-1.6.1-1ubuntu3)

I would be grateful for any help! (Also, are there any online documents explaining the current - that is, ubuntu 9.10 - situation with java? There are some things I don't quite understand... for example, why is sun-java also obviously using libgcj? Shouldn't it have its own runtime libraries?)

David

---

### Post by jakon on 2009-11-30
I have found a solution: [https://bugs.launchpad.net/ubuntu/+source/pdftk/+bug/487922/comments/3](https://bugs.launchpad.net/ubuntu/+source/pdftk/+bug/487922/comments/3)

---

