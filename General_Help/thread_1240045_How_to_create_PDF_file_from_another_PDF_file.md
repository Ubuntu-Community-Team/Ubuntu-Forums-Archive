---
title: "How to create PDF file from another PDF file?"
date: 2009-08-14
forum: General Help
---

### Post by abcuser on 2009-08-14
Hi,
I have a PDF file of 500 pages. I would like to make a new PDF file which would only contain pages 101, 102 and 103.
How to create new PDF file with only 3 pages described above?

My system: Ubuntu 9.04
Regards

---

### Post by lisati on 2009-08-14
One way is to open up the PDF file for viewing, select print, then print to file, and choose a range of pages.

---

### Post by aeiah on 2009-08-14
i use pdftk.

```

pdftk A=big_document.pdf cat A101-103 output selected_pages.pdf

```

its available for windows too

---

### Post by XCan on 2009-08-14
> **aeiah said:**
> i use pdftk.

```

pdftk A=big_document.pdf cat A101-103 output selected_pages.pdf

```

its available for windows too

I too vote for pdftk, it is safer to just extract the pages than sending them through the printer imo.

---

### Post by Bonster on 2009-08-14
PDF shuffler is ez also [http://sourceforge.net/projects/pdfshuffler/files/](http://sourceforge.net/projects/pdfshuffler/files/)

---

### Post by kanikilu on 2009-08-14
I don't see any Ubuntu packages for it yet, but PDF Mod looks promising: [http://gburt.blogspot.com/2009/07/pdf-mod.html](http://gburt.blogspot.com/2009/07/pdf-mod.html)

---

### Post by HermanAB on 2009-08-14
Howdy,

I've never had any luck with editing PDFs with Scribus or OOo, but when all else fails, The Gimp can edit PDFs fairly well.

---

### Post by aethex on 2009-08-14
OOo has a plugin that can import PDFs (Sun PDF Import, I think it was called). I never used it, but you should be able to edit the thing in OOo, if you wanted to make some changes.

You could also google a PDf converter. I use one (only for Windows, unfortunately, but there are plenty) that can convert to HTML and a variety of formats, which can be imported into OpenOffice.

You can then save the document as an ODT for future reference.

---

### Post by abcuser on 2009-08-17
> **aeiah said:**
> i use pdftk.

```

pdftk A=big_document.pdf cat A101-103 output selected_pages.pdf

```


Hi,
I see pdftk is GPL program. So I installed it:
```
sudo apt-get install pdftk
```
and then your above pdftk command. It works excellent.
Thanks a lot.

---

### Post by katon on 2009-09-20
hi, im interested in doing the next thing:
merge 2 pdf that were created with scanner with autofeeder (ADF)
from HP J4580 . It has not the DUPLEX option so i need to scan one side of the pages and then the other side.
How can i merge automatically and simple the two PDF the first is the one side pages the second is the back. 
Thanks

---

### Post by kaibob on 2009-09-20
> **katon said:**
> hi, im interested in doing the next thing:
merge 2 pdf that were created with scanner with autofeeder (ADF)
from HP J4580 . It has not the DUPLEX option so i need to scan one side of the pages and then the other side.
How can i merge automatically and simple the two PDF the first is the one side pages the second is the back. 
Thanks

You can use pdftk to do what you want. If the two PDF files are named odd.pdf and even.pdf, and each PDF file contains 3 pages, the command line would be:

```
pdftk A=odd.pdf B=even.pdf cat A1 B1 A2 B2 A3 B3 output combined.pdf
```

The above quickly becomes cumbersome if more than a few pages are involved. In that case, a simple shell script would be needed.

---

### Post by katon on 2009-09-20
Thanks for the fast response , i understand what you say...
 i do not know how to make scripts,,, but maybe is the time to learn....you tried this things? i mean to merge odd and pair pages?
i think is a great solution because in my country this ALl in one printer cost 100 US dollar and a DUPLEX allinone cost 250-400 US dollar.
I need it to scan duplex to PDF from papers and lectures from the UNiversity.

---

### Post by kaibob on 2009-09-20
> **katon said:**
> Thanks for the fast response , i understand what you say...
 i do not know how to make scripts,,, but maybe is the time to learn....you tried this things? i mean to merge odd and pair pages?...

I tested the command line in my earlier post, and it does work.

---

### Post by kaibob on 2009-09-20
I needed some practice with arrays and wrote the shell script contained below. You have to input the number of pages in odd.pdf and even.pdf as command line parameters. Thus, if odd.pdf contains 5 pages and even.pdf contains 4 pages, you would open a terminal window, change to the target directory, and enter:

```
scriptname 5 4
```

If the number of pages actually contained in odd.pdf or even.pdf is less than what you input on the command line, then pdftk will issue an error and abort. 

```
#!/bin/bash

# Check for command line parameters.
if [ "$2" = "" ] ; then
   echo "Input error"
   exit 1
fi

# Add odd.pdf to array.
i=1
j=0
for i in $(seq ${1}) ; do
   pages[${j}]="A${i}"
   i=$((i+1))
   j=$((j+2))
done

# Add even.pdf to array.
i=1
j=1
for i in $(seq ${2}) ; do
   pages[${j}]="B${i}"
   i=$((i+1))
   j=$((j+2))
done

# Create combined PDF file. 
pdftk A=odd.pdf B=even.pdf cat ${pages[@]} output combined.pdf
```

---

### Post by katon on 2009-09-21
> **kaibob said:**
> I needed some practice with arrays and wrote the shell script contained below. You have to input the number of pages in odd.pdf and even.pdf as command line parameters. Thus, if odd.pdf contains 5 pages and even.pdf contains 4 pages, you would open a terminal window, change to the target directory, and enter:

```
scriptname 5 4
```

If the number of pages actually contained in odd.pdf or even.pdf is less than what you input on the command line, then pdftk will issue an error and abort. 

```
#!/bin/bash

# Check for command line parameters.
if [ "$2" = "" ] ; then
   echo "Input error"
   exit 1
fi

# Add odd.pdf to array.
i=1
j=0
for i in $(seq ${1}) ; do
   pages[${j}]="A${i}"
   i=$((i+1))
   j=$((j+2))
done

# Add even.pdf to array.
i=1
j=1
for i in $(seq ${2}) ; do
   pages[${j}]="B${i}"
   i=$((i+1))
   j=$((j+2))
done

# Create combined PDF file. 
pdftk A=odd.pdf B=even.pdf cat ${pages[@]} output combined.pdf
```

thanks !! i will try it and post
thank you very much

---

### Post by pratikk on 2010-11-04
Hi, I have some DTP PDFs made at 300/2400 dpi. I want to scale them down to screen resolution for download from a Website. AFAIK, image editors are inappropriate for the job since I would have open and save page by page, and there are over 1,000 pages. Any joy to be found in Ubuntu?

Thanks

Pratik

---

### Post by honeybear on 2011-01-09
> **kaibob said:**
> You can use pdftk to do what you want. If the two PDF files are named odd.pdf and even.pdf, and each PDF file contains 3 pages, the command line would be:

```
pdftk A=odd.pdf B=even.pdf cat A1 B1 A2 B2 A3 B3 output combined.pdf
```

The above quickly becomes cumbersome if more than a few pages are involved. In that case, a simple shell script would be needed.

ok but how do you do if you have variable number of pages into :
input1.pdf  # will be the even
input2.pdf  # will be the odd pages ???

---

### Post by perspectoff on 2011-01-09
I like PDF Shuffler and MaxView.

There are several PDF utilities listed at

Ubuntuguide.org at:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#PDF_Files](http://ubuntuguide.org/wiki/Ubuntu:Maverick#PDF_Files)

and Kubuntuguide.org:
[http://kubuntuguide.org/Maverick#PDF_Files](http://kubuntuguide.org/Maverick#PDF_Files)

Of course, as already mentioned, it is trivial to open a PDF document with the default viewer (Okular or Evince) and then just print the pages you want (using the default Print to PDF document that is now a default in Ubuntu) to a new document.

Oh wait, you are using Jaunty. I don't think Print to PDF was a default in Jaunty. Time to update, huh?

---

### Post by Zimmer on 2011-01-09
Have you tried importing them to GIMP?

The pdf pages can be imported as individual layers.......

---

### Post by honeybear on 2011-01-09
We woudl be looking for a solution which would be console based.
It mgiht be easy just how to get number of pages of the pdf
odd.pdf
even.pdf

then I can try to figure out to program you the SH script ...

---

