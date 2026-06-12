---
title: "ubuntu-restricted-extras broke pdftk?"
date: 2010-01-07
forum: General Help
---

### Post by hpstr on 2010-01-07
Hi,

I use Hardy 8.04 LTS, and have pdftk 1.41-2 installed.

Recently I installed recently the ubuntu-restricted-extras package, which began to fiddle with Java, installing the Sun Java JRE even if not required for my tasks.

Now pdftk, that I use to merge PDF files, aborts with error

[FONT="Courier New"]Unhandled Java Exception:
java.lang.ClassCastException: com.lowagie.text.pdf.PdfLiteral cannot be cast to com.lowagie.text.pdf.PdfArray
   at com.lowagie.text.pdf.PdfCopy.addPage(pdftk)[/FONT]

I think I can blame ubuntu-restricted-extras at least for having triggered the problem, as the pdftk and libgcj8-1 packages, which pdftk depends on, seem to be untouched by any upgrade procedures for quite some time.

Purging ubuntu-restricted-extras and the Sun Java JRE does not solve the problem, nor does reinstalling libgcj8-1.

Any hints where to look now?

I saw some hints regarding 9.10, proposing to use other pdftk packages. I would prefer however not to use packages "foreign" to 8.04 LTS.

Thx, Hans

---

