---
title: "How to lower the resolution of all the images in a pdf?"
date: 2010-05-09
forum: General Help
---

### Post by RonB123123 on 2010-05-09
How to lower the resolution of all the images in a pdf?

I searched around and couldn't find an answer to this. I have a pdf file of a textbook that I use in school but each page is an image of 2 pages of the textbook (left page, right page when the book is opened) and each image is of a very high resolution.

I downloaded pdftk and pdfedit but for such a simple problem, I'm having trouble. Is there any way to do this?

I have tried converting the 380 MB PDF file to PostScript but after an hour of doing that, it stopped, and the PostScript only had about 17 pages instead of the 733. So converting it back to a PDF file to utilize pdftk's algorithms would have been worthless. 

I know I could split up the pdf file into sections but I'd rather just scale down all the images, or make them mid quality PNGs or high quality JPGs just so the filesize can be halved. 

~Ron

Edit: I also tried using the compress command using pdftk and after another hour or so it resulted in a higher filesize pdf file. Command I used was:
**pdftk large-book.pdf output new-book.pdf compress**

---

### Post by kaibob on 2010-05-18
You can reduce the size of a PDF with ghostscript by way of the four predefined dPDFSETTINGS settings. The setting that results in the smallest file size is screen and can be implemented as follows:

```
gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -dPDFSETTINGS=/screen -sOutputFile=output.pdf input.pdf
```

If the original PDF is color and you can live with grayscale, the following command should further reduce file size:

```
gs -sDEVICE=pdfwrite -dNOPAUSE -dQUIET -dBATCH -dPDFSETTINGS=/screen -sColorConversionStrategy=Gray -dProcessColorModel=/DeviceGray -sOutputFile=output.pdf input.pdf
```

There is no guarantee that either of these commands will significantly reduce file size, because the reduction in file size is dependent on the resolution and other characteristics of the input PDF. But, it's easy to give these commands a try. 

Just for reference, the following page contains a chart that details the four predefined dPDFSETTINGS settings and the individual parameters that each setting modifies:

[http://pages.cs.wisc.edu/~ghost/doc/cvs/Ps2pdf.htm](http://pages.cs.wisc.edu/~ghost/doc/cvs/Ps2pdf.htm)

---

### Post by eumetaxas on 2010-06-18
> You can reduce the size of a PDF with ghostscript by way of the four predefined dPDFSETTINGS settings. The setting that results in the smallest file size is screen and can be implemented as follows:


Thank you!

---

### Post by RonB123123 on 2011-02-26
A better technique is to convert the PDF to a DJVU file. I love DJVU files because they are a lot faster and smaller in filesize. 

sudo apt-get install pdf2djvu

> 
pdf2djvu -o NAME-OF-NEW-FILE.djvu NAME-OF-PDF.pdf


Ron

---

