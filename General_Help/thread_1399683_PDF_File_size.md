---
title: "PDF File size"
date: 2010-02-06
forum: General Help
---

### Post by manishshrd on 2010-02-06
I would like to convert doc files to pdf files on my Ubuntu 9.04. Have tried using Open Office by exporting it to pdf format, however, it converts a 23kb doc file to 150kb pdf file. I have tried reducing the dpi to 75 however the pdf files doesn't reduces in size much and quality of print is really bad.

Im using pdfOnline.com at the moment to convert my doc files to pdf, which does a fantastic job. 23kb doc files converts to 12kb pdf file with quality of 300 dpi color. However, I don't have internet access everywhere and I would like to make pdf files while Im not on the net.

I have also tried printing to ps format and converting it to pdf, however the print is in gray scale and the file size is still larger than the original doc file.

Can anyone help me to make doc file to pdf with smaller file size on Ubuntu 9.04?

---

### Post by kaibob on 2010-02-06
You can print to cups-pdf. I ran a test with a 4-page OpenOffice Calc spreadsheet and got the following file sizes:

22 KB - OpenOffice document

47 KB - printed to cups-pdf

156 KB - created with OpenOffice export as PDF option

If cups-pdf is not installed, I believe it's in the repo's and can be installed with synaptic. You may have to create the PDF directory in your home directory. You could get the cups-pdf file sizes even smaller by changing the settings in the cups-pdf configuration file.

---

### Post by hawthornso23 on 2010-02-06
[http://www.aivosto.com/vbtips/pdf-optimize.html](http://www.aivosto.com/vbtips/pdf-optimize.html)

... explains why pdf files can grow to be so large, and offers suggestions for stopping it from happening. Finishes with an example of two essentially identical looking pdfs to illustrate the technique. One is 6kb and the other is 4500% larger at 273kb.

---

### Post by manishshrd on 2010-02-06
> **kaibob said:**
> You can print to cups-pdf. I ran a test with a 4-page OpenOffice Calc spreadsheet and got the following file sizes:

22 KB - OpenOffice document

47 KB - printed to cups-pdf

156 KB - created with OpenOffice export as PDF option

If cups-pdf is not installed, I believe it's in the repo's and can be installed with synaptic. You may have to create the PDF directory in your home directory. You could get the cups-pdf file sizes even smaller by changing the settings in the cups-pdf configuration file.
Printing to cups-pdf printer outputs smaller pdf files. I should have tried it before posting query. Thanks for your help.

Cheers
Manish

---

### Post by ahalin on 2011-02-02
For word documents with pictures in them I found that *> File > print > cups-pdf* produced a larger file than the original, as did the default settings in > *File* > *Export as PDF* in OpenOffice. 

However, when you click on > *Export as PDF* an options window opens. Reduce the image size on the *JPEG Compression* (middle of the *General* tab in the options window) to 33% or something like that and bingo, you have a smaller file!

):P

---

