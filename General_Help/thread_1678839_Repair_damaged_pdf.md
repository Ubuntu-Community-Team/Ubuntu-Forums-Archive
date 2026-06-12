---
title: "Repair damaged pdf"
date: 2011-01-31
forum: General Help
---

### Post by whowinsdares on 2011-01-31
I have an old USB that I recently recovered about 180 PDF files from. It was mixed up in raw data and I managed to extract the files using a program on windows in a net cafe.
I then had to format the USB to be usable.

Now I have the USB drive back at my house, of the 182 PDF files, 8 of them are unreadable and come up as damaged.

I can't open the files with Abode, Gimp, or any other PDF program.

For some reason, these are all the largest PDF files recovered. There is probably some program on windows that could recover the files but I am not running windows and it takes me hours to travel to a net cafe..

---

### Post by HermanAB on 2011-01-31
Hmm, note that most Linux programs use the same ghostscript PDF backend.  So if one won't work, the others won't either.

The exception is Xpdf.  Install Xpdf and try it.  I have found in the past that it seems to be more robust than ghostscript.

---

### Post by whowinsdares on 2011-01-31
Thanks,

I tried that but it didn't work either - but thanks for replying!

---

### Post by oldos2er on 2011-01-31
Have you tried pdftk? Its description says it, among other things, repairs corrupted PDFs where possible.

---

### Post by arnaudj on 2011-07-21
where possible, was not enough in my case.
for pdftk:

```
Error: Failed to open PDF file: 
   w.pdf
Done.  Input errors, so no output created.

```

for xpdf :

```
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
```

still searching

---

