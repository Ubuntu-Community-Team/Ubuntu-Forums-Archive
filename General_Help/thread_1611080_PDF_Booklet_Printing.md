---
title: "PDF Booklet Printing"
date: 2010-11-01
forum: General Help
---

### Post by Neek0 on 2010-11-01
I need to print some rather large pdf files 200+ pages into books. i have found ways to print booklets, but they print the first and last pages on one piece of paper. that will not work for this large of a document.

I'd like to print every _sheet_ as a separate
fold:

Sheet 1, side 1:        4; 1
Sheet 1, side 2:        2; 3
Sheet 2, side 1:        8; 5
Sheet 3, side 2:        6; 7

instead of the normal, put all sheets together and fold at same time:

Sheet 1, side 1: 8; 1
Sheet 1, side 2:        2; 7
Sheet 2, side 1: 6; 3
Sheet 3, side 2: 4; 5


i've tried adobe reader, okular, psbook & psnup, they all turn out the booklet format where the entire book is folded at once, rather than each individual page being folded.

---

### Post by blueridgedog on 2010-11-01
Not a solution, but a suggested alternative:

Split the pdf into 8 or 10 chunks with pdftk then booklet print the chunks, into 8 or 10 "signatures" that can then be bound together or assembled in a binder.

---

### Post by mike555 on 2010-11-01
You could try Scribus 138

---

### Post by Neek0 on 2010-11-22
well, i found a way to do it that is not terrible.

i used open office spreadsheet (or microsoft excel) to create a file with my order 4 1 2 3 using =concatenate and saved as a .csv.
i then used sed to replace all of the ","s with a single space. by the way, i made this file go to 1000 so i only had to do it once. copy file.csv to file.txt so it opens in a text editor instead of open office.now, just check how many pages you have in your pdf and copy to that number from your .txt file and past it into the "4 1 2 3" space in the code below and print your new file 2 per page. (if anyone actually wants an explanation of how let me know.

use pdftk:

```
pdftk file.pdf cat 4 1 2 3 output new-file.pdf
```

---

### Post by brown12 on 2011-01-04
Try Adobe PDF Reader. 

In the print dialog, I am able to select booklet printing.
> Print ...
> Page Handling
> Page Scaling: Booklet Printing 

In order to rotate pages correctly, select landscape orientation (even though each page of the original PDF is 8.5x11 portrait) and leave "autorotate pages" checked.

For long documents, test first on Pages 1-4 or Pages 1-8 to ensure you've got the page rotations correct.

From OpenOffice, export to PDF and then print booklet format via Adobe Reader. There is a brochure dialog inside of OpenOffice, but I find it easier to let Adobe work out the booklet settings.

Works on Lucid 10.04 / acroread 9.4.1

---

### Post by keenanan3j on 2011-08-03
Those replies and answers are definitely helpful! Thanks guys!

---

### Post by victor.cighir on 2011-08-29
I had to print something that I will use for a very short while and thought I will do it using booklet. My files where already in .pdf format. So I went about writing a python script using pyPDF. It was very rudimentary but did it's job well.

Then I tried a pdfEdit script called *[booklet.qs]("http://pdfedit.petricek.net/wiki/ScriptLibrary")* Works also fine.

Then I found a very easy to use method on
*[Scribus.net How to make a booklet]("http://wiki.scribus.net/canvas/How_to_make_a_booklet")* under the heading "*Method A-2: using ps2book*"

Perfect script to create ready for print booklets in .ps or .pdf format.
Download script source code from *[ps2book]("http://www.capca.ucalgary.ca/~wdobler/utils/ps2book")* Source code itself has helpful info and some examples. Basic usage should do it. I copied the source code into a file called ps2book.pl, then changed permissions and made it executable. Finally from terminal run it using 
```
perl ./ps2book.pl -p a4 -F0.9 test_book.ps
```
-p a4 stands for DIN A4 standard size
F 0.9 is a scale factor that I found good for my documents. The author examples are with F0.87.

Good luck printing!

---

