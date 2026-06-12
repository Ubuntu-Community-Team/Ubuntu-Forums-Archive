---
title: "CHM to PDF"
date: 2010-08-01
forum: General Help
---

### Post by arashiko28 on 2010-08-01
So I followed every step and at the end I get an error message and no PDF.

I installed libchm-bin, then extracted the chm to a folder, then installed htmldoc and then, when I load it, I choose book and get an error message about no pages being generated and if I remember choosing webpage mode. 
Any Ideas? I really need this!

---

### Post by kureta on 2010-08-02
Hi, you can download chm2pdf from "Ubuntu Software Center" and try using that.
Check [this]("http://www.karakas-online.de/forum/viewtopic.php?t=10969") out for usage info.

---

### Post by dongiulio on 2011-02-19
I've just made it, to convert a full CHM to PDF format so I can read it nicely on my Kindle. 

I want to report here the steps I did, so it may be helpful to others.

In summary the steps involved: 
[LIST=1]
[*]extracting the HTML from the CHM
[*]Sorting the HTML files so the alphabetical order was the same as the Page order
[*]converting the HTML files to an unique, easy to read PDF file
[/LIST]

To begin, I used the great library for CHM: libchm-bin
installed with: 
```
sudo apt-get install libchm-bin
```
 
The use is very simple: 

```
extract_chmLib <path to the chm file> <directory for the resulting HTML files>
```

*Note* that the chm file may contain many many html files, so you better use as output directory a specifically created, empty one. 

after this, your destination directory now contains an directory structure, and in one of the subdirectories a long list of HTML files that are the sections of your chm. You can use your favorite browser to see them. 

At this point the HTML files are ready to be converted into a single PDF. To do this I used the powerful "htmldoc", which I installed with: 

```
sudo apt-get install htmldoc
```

This can be invoked by the simple 0 parameters htmldoc command, and this will open a nice user interface. After trying a bit with the gui, I realized that there was no simple way to import all my html files, and sorting them properly. So I resorted in working from the console. I'll show you how: 

The basic way to use htmldoc to generate a pdf from command line is the following: 

```
htmldoc -t pdf13 --webpage -f myFile.pdf orig.html
```

This will take the orig.html file and generate a pdf file called myFile.pdf. 

Everything fine, but this is not enough for me, as my extracted chm contains many html files, and I want them all in one pdf. 

So I varied the command above by inserting a wildcard: 
```
htmldoc -t pdf13 --webpage -f myFile.pdf *.html
```

This made a unique PDF file containing all my html files, but they were not in the order I wanted them. 

so I started renaming, one after the other all the html files, so that their alphabetic ordering would be the same as the order I want them in the PDF. 

For example toc.html is a page I want to see before conclusions.html, therefore I renamed both files to: 
atoc.html
zconclusions.html
so that with "ls -1" I'd see them listed in the same order I want them to be in the PDF.

At this point the last command above: 
```
htmldoc -t pdf13 --webpage -f myFile.pdf *.html
```

made a single PDF with all my html files and in the right order for me. Although it was all a bit small and hard to read. After a bit of trial and error I found the configuration perfect for my kindle. that I can use to read my chm book easily, and with images too. The final command I used was the following: 

```
htmldoc -t pdf13 --color --webpage --compression --fontsize 18.0 --browserwidth 824 --right 5mm  --left 5mm -f ../myBook.pdf *.html
```

Uploaded the pdf file to my kindle and enjoyed the read. 

I hope it all works good for you as it did for me.

---

### Post by kwacka on 2011-02-19
I haven't tried a .chm to .pdf conversion, but use **calibre** to convert various formats to epub.

It does handle both pdf & chm, and is in repositories.

---

