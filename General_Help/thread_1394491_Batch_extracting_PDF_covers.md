---
title: "Batch extracting PDF covers?"
date: 2010-01-30
forum: General Help
---

### Post by linuxgeekery on 2010-01-30
I have a large set of PDF magazines and books that I'd like to extract the cover from—all of them, the cover is page one of the PDF.  However, even with the combined forces of Google and the Imagemagick man page, I haven't found a suitable way to do this.

Any suggestions?

---

### Post by NightwishFan on 2010-01-30
In a terminal:
```
cd /directory/of/pdfs
```
then:
```
pdfimages -f 1 -l 1 *.pdf DIRECTORYTOSAVE
```

Might have to tweak the command a bit, didn't test it.

EDIT: I think you cannot use *.pdf... Have to name them 1 by 1 ;/. Ill look around.

---

### Post by linuxgeekery on 2010-01-30
Thanks! I didn't even know about pdfimages.  Also, *.pdf doesn't work, you have to iterate over them in a loop.

```

for i in *.pdf; do pdfimages -f 1 -l -1 $i directory/; done

```

---

### Post by NightwishFan on 2010-01-30
Glad you solved it.

As a note, the pdfimages extracts all individual images, if the cover is made up of more than one, it may be separate. There is another command called "pdftoppm" which allows you to set .png as an output, and I believe it may save the whole page. Worth a try.

---

