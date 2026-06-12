---
title: "Merge files into a single pdf"
date: 2010-09-18
forum: General Help
---

### Post by Chethan S on 2010-09-18
[LIST=1]
[*]I have several image files accumulated as a result of taking screenshots. I want to merge all of them into a single pdf file. How can I do that?
[*]I save webpages in .mht format using UnMHT addon in firefox. Is there any way to merge several mht files into a single pdf?
[/LIST]

---

### Post by ShokTHX on 2010-09-18
One way to put several images into one PDF would be to put them in an Open Office document and export the PDF.
I know that's probably not what you are looking for but it is an option.
There are several PDF programs in the Ubuntu Software Center have you not had any luck with them?
As for printing the .mht files:
Install cups-pdf from Synaptic and you should be able to print them out as PDF's and combine them into 1 PDF in another PDF program. You could probably do this with the screenshots too.

---

### Post by Chethan S on 2010-09-18
The option provided by you regarding printing mht files is quite ok but however if there is some option to print all mht files together which is accumulated as a result of few months of work it would be nice. Such a thing would be possible with Adobe Acrobat but I am looking for a solution in ubuntu exclusively.

---

### Post by kikazaru on 2010-09-18
You can do this with convert (ImageMagick) and pdftk (both of which have convenient ubuntu packages).

# To convert an image to a pdf file suitable for building a pdf

convert image.png image.pdf

# To split a PDF file into individual pages (each as a PDF file)
pdftk original.pdf burst output burst_%04d.pdf

# To merge pages representing PDF files back together

pdftk burst_0001.pdf burst_0002.pdf burst_0003.pdf output final.pdf

Note: they don't have to be individual pages, and you can also stamp an overlay image on top of a PDF if you want to (I looked this stuff up so I could stamp semi-transparent highlighter mark images onto a PDF).

ps. Sorry, didn't notice you were staring with mht files. convert can't handle them, but there seem to be plenty of ways to convert them to images:

[http://html-to-image.acasystems.com/faq-convert-mht-to-image.htm](http://html-to-image.acasystems.com/faq-convert-mht-to-image.htm)

---

### Post by LeoBastos on 2010-10-04
I have the same problem. I need to merge pdf files. I generally use the code

```
gs -q -sPAPERSIZE=letter -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=out.pdf in1.pdf in2.pdf in3.pdf ...
```However, I have a lot of files, named as 0001_something.pdf, 0002_somethingelse.pdf,...,0900_somethingdifferent.pdf. 

Any thoughts?

ps: Thanks for the pdftk tip. I found some examples in the [pdftk page]("http://www.pdflabs.com/docs/pdftk-cli-examples/") where I could some my problem. 

Cheers!

---

### Post by babis79 on 2010-11-16
Try Couturier

[http://www.omgubuntu.co.uk/2010/09/icombiner-for-pc-linux/](http://www.omgubuntu.co.uk/2010/09/icombiner-for-pc-linux/)

---

### Post by toshko3 on 2010-12-22
> **babis79 said:**
> try couturier

[http://www.omgubuntu.co.uk/2010/09/icombiner-for-pc-linux/](http://www.omgubuntu.co.uk/2010/09/icombiner-for-pc-linux/)

yeah! Definitely!

---

### Post by kgarbutt on 2010-12-22
Hi,

pdftk works really well turning many pdfs into one pdf. It works from the terminal, and you can install it like this:

sudo apt-get install pdftk

Now to combine multiple pdfs you do this from the terminal:

pdftk 1.pdf 2.pdf 3.pdf cat output 123.pdf

or every pdf in a directory like this:

pdftk *.pdf cat output all.pdf

You can check out pdftk here:
[http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/](http://www.pdflabs.com/tools/pdftk-the-pdf-toolkit/)

Good luck, Ken

---

### Post by youngmix on 2013-03-08
question 1:
cd (navigate within the terminal) your way to the folder holding the .pdf files

use this command
[B]pdftk *.pdf cat output merged.pdf

[/B]'merged.pdf' is where you name the file. You can write:

pdftk *.pdf cat output book01.pdf

or whatever.

Two sources carry this info, and the TLD's (top-level domains) are useful for handy BASH commands:
[http://ubuntuhowtos.com/howtos/merge_pdf_files](http://ubuntuhowtos.com/howtos/merge_pdf_files)
&&
[http://maketecheasier.com/combine-multiple-pdf-files-with-pdftk/2010/02/22](http://maketecheasier.com/combine-multiple-pdf-files-with-pdftk/2010/02/22)

---

### Post by youngmix on 2013-03-08
Question #2:
Try--

[COLOR=#111111][FONT=Consolas]html2ps $mht; lpr $s -P PDF

[/FONT][/COLOR]Navigate to the desired directory, and run the command.

I've never tried this. I have not tested html2ps with .mht files, but try it.

---

### Post by mbeach on 2013-03-08
For the first part of your question you may be interested in PDF Split and Merge.

[http://www.pdfsam.org/](http://www.pdfsam.org/)

Edit: disregard - I misread your source files as pdf not images.

---

### Post by tgalati4 on 2013-03-08
I love the fact that there are a dozen ways to do the same thing in linux.  And because this thread is 2 years old, it will be closed soon.

But not by me.

---

