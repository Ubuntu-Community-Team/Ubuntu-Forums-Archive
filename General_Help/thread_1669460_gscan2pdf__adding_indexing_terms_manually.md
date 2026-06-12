---
title: "gscan2pdf : adding indexing terms manually?"
date: 2011-01-17
forum: General Help
---

### Post by acpcalif on 2011-01-17
gscan2pdf can do OCR, so in theory the resulting pdfs should be indexable (e.g, by recoll) based on the contents of the scans.
But in practice I've found this doesn't work well for me:

[LIST]
[*]Often I want to index on additional terms / phrases not in the document
[*]The OCR usually has a lot of errors and is often mostly junk -- happens for all supported engines
[*]Even when OCR gives useful results, it takes a long time to complete, slowing my workflow
[/LIST]

I'd find it useful to skip OCR and be able to just add some text to the PDF that recoll could index on.

Does gscan2pdf already somehow support adding such text?

Or is there some equivalent out there of the following hypothetical command line, that I could run on the output of gscan2pdf?

```
add_text_to_pdf_for_indexing "Jane co-pay receipt nov 5 2010 dr. jones" myscan.pdf
```

Or other suggestions entirely?

Thanks!

---

### Post by acpcalif on 2011-01-17
Found two solutions:

[LIST]
[*]In gscan2pdf, when saving as pdf, specify "keywords" in the pop-up dialog. Recoll does index them.  Prior to my post I thought I had tried this without success but it seems to work for me now (maybe I hadn't re-indexed).

[*]Use pdfedit to write a text note in a margin on one of the scanned pages.
[/LIST]

---

