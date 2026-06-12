---
title: "HOWTO: Split double-page PDF files down the middle!"
date: 2009-12-09
forum: General Help
---

### Post by CupofDice on 2009-12-09
**Tired of those double page PDF files? This is the tip/tutorial/whatever for you! Had to sorta figure this all out myself, since everything I came across didn't have actual instructions. :/**

**Simple Disclaimers:**

1. Make a backup of the original file and put it somewhere.
2. Just make a folder in your Home so using the terminal will be easier.

**Instructions:**

Use pdfshuffler (in the Repository) and take the original file and crop it 50% (if the text is dividing straight down the middle) from the right, then save as "file1.pdf". Then do the same again with the original file, this time cropping from the left, and saving it as "file 2.pdf".

Now the really fun part >_<. Install pdftk (also in the repositories), and with that we will copy/paste this command into the terminal: ptftk "file1.pdf" burst. Make sure you are in the right folder. Move all of the new files into a subfolder, then burst "file2.pdf". 

With the files you put in the subfolder, rename them with KRename (or whatever mass renamer you're using). You want it to be all odds (1, 3, 5, 7). Figure out how to use the renamer for yourself :P. Then rename the second set of files by even numbers (2, 4, 6, 8 ). Make sure your files aren't backwards or anything by looking at the PDFs and making sure pg 1 goes to pg 2 which goes to pg 3. There should be no problems though. 

From here it's easy again. Take the second set and add them to the first in the subfolder (or vice versa). Throw them all back into pdfshuffler, delete the blank pdf pages if you want to (for ppl like me with ebook readers who don't want to wait on the e-ink just to show a blank page :P ). Make a new pdf with pdfshuffler, and voila. All done. :D 

Hope this helps someone. ;)

---

### Post by VetaSu on 2010-01-23
Many thanks! worked wonders!

one of the commands should be 
pdftk "file1.pdf" burst

instead of ptftk

---

### Post by skywriter on 2010-04-05
Which repository to use to install **pdfshuffler**? I have searched in 9.04's default repos unsuccessful.

Already found [separate deb](http://sourceforge.net/projects/pdfshuffler/files/pdfshuffler/0.5/pdfshuffler_0.5-0_all.deb/download).

---

