---
title: "How to: Fix Google PDF ebooks to display images or to use on Kindle"
date: 2011-09-16
forum: General Help
---

### Post by nathandetroit on 2011-09-16
The problem: Google books in PDF format do not display contained images when viewed in Evince document viewer, or when transferred to a Kindle ebook reader. The reason for this is that Google saves images in PDF files in jpeg2000 format. Some versions of Evince (see note below) cannot display jpeg2000. The Kindle ebook reader can display PDF files, but contained images in jpeg2000 format show up as blank spaces.

Many Google books are available for free in PDF format. These books can be easily transferred to the Kindle ebook reader (most easily using the Calibre ebook manager). I attempted to fix the problem with jpeg2000 images in three ways, with results as follows:

1) Using ghostscript

This was the most successful. Ghostscript can be run from a terminal using the following command:

   ```
gs -dNOPAUSE -dBATCH -dPDFSETTINGS=/ebook -sDEVICE=pdfwrite  -sOutputFile=output.pdf input.pdf
```

where input.pdf is the name of the PDF file to be converted, and output.pdf is the resulting converted file.  This method converts embedded jpeg2000 images to "conventional" jpeg images. The resulting output file will be larger (how much larger depends upon how many images are in the input file). The output file displays images in Evince and on the Kindle reader.

2) Using Foxit PDF reader

The Foxit PDF reader (proprietary, but free), displays Google PDFs nicely. The PDFs can be converted to "conventional" PDFs by opening the file in Foxit and "printing" it to a PDF file. This appeared to work, but Foxit crashed with very large PDF files. I did not test the size limit for this method, but I note that the 1,051 fle I was attempting to convert caused Foxit to crash, though I could convert selected pages from the same file with no problem.

3) Using built-in Calibre conversion

Converting the PDF file to Mobi in Calibre did not work - the resulting file was a mess, and images still did not display. I also tried "converting" from PDF to PDF; although Calibre cranked away dutifully and produced an output file, it appeared to be no different from the original.

============================

Note: The problem with Evince exists in Ubuntu 10.04, but appears to have been fixed in Ubuntu 11.04. While I did not test this, I assume that even with Ubuntu 11.04, the problem with transferring to a Kindle would still exist, on the assumption that the Kindle PDf viewer does not support jpeg2000.

This was tested with Kindle version 3.1 (558700031)

---

