---
title: "problems creating pdf"
date: 2010-05-19
forum: General Help
---

### Post by gregorye70 on 2010-05-19
Greetings
I'm running karmic koala 9.10
I installed  cups-pdf and it now shows as the default in my printer list, but when I choose the file type drop down from the printer dialog box it only has ps as an option so when I save it  I end up with a post script file not a pdf.

They aren't the same thing?  What have I not done to get a pdf option?

Thanks

---

### Post by efflandt on 2010-05-19
In what application are you seeing that drop down list for file type?

I don't even see a drop down list for file name or type when printing from the print dialog for PDF printer.  Are you selecting "Print to file" instead of the "PDF" printer?  The PDF printer automatically names the pdf files it generates and puts them in ~/PDF/ directory.

---

### Post by gregorye70 on 2010-05-19
I'm trying to save a open office word processing document so its the print dialog box in the word processor

---

### Post by luigi_mb on 2010-05-19
A simple work-around. View the .ps file with gv (it's in the repos). Then in gv save the file to .pdf.

/luigi

---

