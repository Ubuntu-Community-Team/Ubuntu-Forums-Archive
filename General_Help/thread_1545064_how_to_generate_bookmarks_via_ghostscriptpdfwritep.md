---
title: "how to generate bookmarks via ghostscript/pdfwrite/pdfmark"
date: 2010-08-03
forum: General Help
---

### Post by maggoteer on 2010-08-03
Never mind - SOLVED! creating a pdfmark file wasn't (for my simple purpose) as difficult as I thought.

I simply switch my ghostscript invocation to:

gs -dBATCH -dNOPAUSE -sPAPERSIZE=letter -sDEVICE=pdfwrite -sOutputFile="MASTER.pdf" $(ls CH*.pdf) pdfmarks

where I have a text file named "pdfmarks" that contains the following
[/Title (Prologue) /Page 1 /OUT pdfmark
[/Title (Chapter 1) /Page 5 /OUT pdfmark
[/Title (Chapter 2) /Page 27 /OUT pdfmark
[/Title (Chapter 3) /Page 44 /OUT pdfmark
[/Title (Chapter 4) /Page 60 /OUT pdfmark
[/Title (Chapter 5) /Page 76 /OUT pdfmark
[/Title (Chapter 6) /Page 91 /OUT pdfmark
[/Title (Chapter 7) /Page 107 /OUT pdfmark


Original question:
I've been using ghostscript to merge together a number of individual chapter pdfs into one large pdf ala:

gs -dBATCH -dNOPAUSE -sPAPERSIZE=letter -sDEVICE=pdfwrite -sOutputFile="MASTER.pdf" $(ls CH*.pdf)   

Works great - makes me love the command line. 
Now I'm trying to figure out how to add a bookmark into the merged pdf for each chapter. My searches lead me to "pdfmark" - but for the life of me, I have made no progress in understanding pdfmarks format. Bluntly, all the instructions I've found presume far more knowledge than I have about matters postcript, tex, etc. 



Thanks
Michael

---

