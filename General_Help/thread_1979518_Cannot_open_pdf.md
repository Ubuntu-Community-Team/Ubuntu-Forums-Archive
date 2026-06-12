---
title: "Cannot open pdf"
date: 2012-05-13
forum: General Help
---

### Post by krytorii on 2012-05-13
For some reason, both okular and document viewer have decided to stop opening pdf files. I've tried opening them from the program already running, or from right clicking a file. I've tried uninstalling and reinstalling both okular and document viewer.

Both were working fine earlier, this change seems to have come for no apparent reason.

---

### Post by hal8000 on 2012-05-13
Try starting from the terminal e.g.

okular /path/to/my/file.pdf


Replace /path/to/my/file.pdf with appropriate path and document name, and post any error messages from the terminal.

---

### Post by krytorii on 2012-05-13
From okular
```
okular(4588)/kdeui (kdelibs) KXMLGUIClient::~KXMLGUIClient: 0xe3ce10 deleted without having been removed from the factory first. This will leak standalone popupmenus and could lead to crashes.
```From document viewer/evince:
```
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table
Error: PDF file is damaged - attempting to reconstruct xref table...
Error: Couldn't find trailer dictionary
Error: Couldn't read xref table

(evince:4600): EvinceView-CRITICAL **: ev_document_model_set_document: assertion `EV_IS_DOCUMENT (document)' failed

** (evince:4600): CRITICAL **: ev_sidebar_page_support_document: assertion `EV_IS_DOCUMENT (document)' failed

(evince:4600): EvinceDocument-CRITICAL **: ev_document_get_n_pages: assertion `EV_IS_DOCUMENT (document)' failed

(evince:4600): EvinceDocument-CRITICAL **: ev_document_get_max_page_size: assertion `EV_IS_DOCUMENT (document)' failed
```This comes from any PDF, so it's not the file.

---

### Post by krytorii on 2012-05-14
Any suggestions at all? I kinda need pdfs for a lot of things, and I don't want to have to reinstall over something so silly.

---

### Post by drmrgd on 2012-05-14
Does this happen with all .pdf files, or just this one in particular?  The error you're getting suggests there's a problem with this .pdf file being damaged.

---

### Post by Pronker on 2012-09-12
I'm having the same problem opening _some_ pdf files... It happens with files that I have annotated with iAnnotate on my iPad, but not always. There are some pdfs where I've done heavy editing where they still open fine in evince. Curiously, they open just fine in Adobe Acrobat reader. 

I'm assuming that in my case it has to do with how iAnnotate has changed some of the metadata? But no clue how or why... the iAnnotate crew just stated that they were unable to reproduce the problem with the PDFs I sent them. They don't open in the google document viewer (via gmail) either.

---

