---
title: "Program for cutting together PDF files?"
date: 2010-08-18
forum: General Help
---

### Post by -nat- on 2010-08-18
I don't know if there is anything out there that can do this, but I'm looking for something that will allow me to grab pages from various PDF files and combine them into a single document.

Simply copying and pasting from Document Viewer to OpenOffice is no use, as I want to copy the graphics from the page as well.
Exporting the pages as images is also not the best option, due to the fact that I can no longer search (ctrl-F) through the document to find certain words.

---

### Post by nbkr on 2010-08-18
There is a very good console tool for this: pdftk

To combine pages you could use a command like this.

```

pdftk A=first.pdf B=second.pdf C=third.pdf cat A1-20 B3 C17-20 B4 output new.pdf

```

You will get a new file, called "new.pdf" that has the first 20 pages of PDF A, than Page 3 of PDF B, than the pages 17-20 from PDF C and finaly page 4 from PDF B.

---

### Post by -nat- on 2010-08-18
> **nbkr said:**
> There is a very good console tool for this: pdftk

To combine pages you could use a command like this.

```

pdftk A=first.pdf B=second.pdf C=third.pdf cat A1-20 B3 C17-20 B4 output new.pdf

```

You will get a new file, called "new.pdf" that has the first 20 pages of PDF A, than Page 3 of PDF B, than the pages 17-20 from PDF C and finaly page 4 from PDF B.

I was actually looking for something with a GUI, as I'm not sure on the exact pages I want from the 100+ documents, but I'll try pdftk if nothing else comes up. :)

---

### Post by jamie_alexander on 2010-08-18
KWord is a KDE application that has a pdf &#8220;import&#8221; feature which lets you import either entire pdf documents or just a few pages from a pdf document while preserving the formatting! or so I'm told! Might be worth trying though.

And this site might be useful too

[http://www.freefileconvert.com/](http://www.freefileconvert.com/)

---

