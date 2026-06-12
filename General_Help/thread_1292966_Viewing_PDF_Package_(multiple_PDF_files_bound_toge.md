---
title: "Viewing PDF Package (multiple PDF files bound together)"
date: 2009-10-16
forum: General Help
---

### Post by bkbk on 2009-10-16
I downloaded a PDF file, but when I open it with Evince, the page says, "Multiple files are bound together in this PDF Package" followed by a recommendation to get Adobe Reader 8. It says if I already have Reader 8 to "click a file in this PDF Package to view it."

Which software can I use to view the PDF files (other than Adobe Reader 8)? Right now, I don't even see a list of files contained in the package.

Thx.

---

### Post by blueridgedog on 2009-10-16
I can't sat that it will work, but:

```
ghostscript /path/to/your/pdf/file.pdf
```

---

### Post by sven 22 on 2009-12-18
> **bkbk said:**
> I downloaded a PDF file, but when I open it with Evince, the page says, "Multiple files are bound together in this PDF Package" followed by a recommendation to get Adobe Reader 8. It says if I already have Reader 8 to "click a file in this PDF Package to view it."

Which software can I use to view the PDF files (other than Adobe Reader 8)? Right now, I don't even see a list of files contained in the package.

Thx.

Hi.

I have exactly the same challenge. Did you ever get this to work?

Thanks in advance.

Sven

---

### Post by evaitl on 2010-03-20
Given foo.pdf that does this on karmic I did:

[FONT="Courier New"][INDENT]ps2pdf foo.pdf
pdf2ps foo.ps
[/INDENT][/FONT]
foo.pdf is now readable by evince. I think everything in the original pdf was in there.

---

