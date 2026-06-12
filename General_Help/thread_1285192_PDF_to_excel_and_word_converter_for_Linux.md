---
title: "PDF to excel and word converter for Linux"
date: 2009-10-07
forum: General Help
---

### Post by anirban.sg84 on 2009-10-07
Hi all, 
 Is there any PDF to MS Excel and PDF to MS Word converter for Linux? I require one very urgently please. Our client has Unix server and there I have to write a code to convert PDF files to Excel and as well as to Word Document. But I am not being able to find a suitable software for Linux. Any suggestions please?

---

### Post by Vaphell on 2009-10-07
wine + some converter from windows world?

---

### Post by anirban.sg84 on 2009-10-07
I haven't checked anything with wine till now. Actually I am downloading wine from Ubuntu repositories. But I am not finding any suitable pdf to excel/word converter listed in the wine database. May you guys can suggest one..

I am thinking of trying PDFCONVERTER with wine.. Though PDFCONVERTER is not listed in the wine database, I am not pretty sure whether it will work with wine or not.

---

### Post by QIII on 2009-10-07
Open Office has a word processor (Write) and a spreadsheet (Calc) that are almost fully compatible with Word and Excel.

You may be able to use OO to convert pdf files to compatible file types (I know you can save Open Office Write files as .doc files) and use those.

---

### Post by Vaphell on 2009-10-07
well, if you don't try, you'll never know :-)

---

### Post by mechro on 2009-10-07
OpenOffice has an extension available to import PDF's...

[http://extensions.services.openoffice.org/node/2587](http://extensions.services.openoffice.org/node/2587)

Once imported into OpenOffice you can then save as a Microsoft document.

... of course it may not work or there could be formatting issues.

---

### Post by anirban.sg84 on 2009-10-07
Hi,
    As I have mentioned in my first post, that _**I have to write a code to call the exe file**_.While my code is fine and tested, I am not finding a software that my code can call and execute. Will the OO's feature you are talking about, be able to get executed from a program? My client _**does not**_ want to manually convert pdf files to word/excel.

---

### Post by QIII on 2009-10-07
I suspect that OO documentation can tell you about OOs APIs.

---

### Post by efflandt on 2010-12-21
This probably all assumes that the PDF files were originally directly converted to PDF files that include text.  If they are scanned files, you would need an OCR program to try to convert graphics to text.

---

