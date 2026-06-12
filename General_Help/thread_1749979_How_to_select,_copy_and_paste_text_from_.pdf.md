---
title: "How to select, copy and paste text from .pdf"
date: 2011-05-05
forum: General Help
---

### Post by satimis on 2011-05-05
Hi,

Ubuntu 11.04
Adobe Reader 9

I can't highlight/select text and copy and paste it to another file.  It worked for me on previous version.  Please advise how to make it.

After installing OpenOffice pdf extension on LibreWrite I can import .pdf but still I can't find the select/copy/paste functions.  Please advise.

TIA

B.R.
satimis

---

### Post by satanselbow on 2011-05-05
I would install gscan2pdf through the software centre, load your PDF up and ocr it to extract the text content ;) - selecting the tesseract engine for ocr usually produces the best results and is installed as part of gscan2pdf though not selected by default. 

It is possible that the PDF in question is comprised of images (ie a scanned magazine) rather than text objects.

---

### Post by Lars Noodén on 2011-05-05
Try another PDF viewer like Evince or Okular.

---

### Post by satimis on 2011-05-05
Hi,

Thanks for your advice.

> **satanselbow said:**
> 
- snip -

It is possible that the PDF in question is comprised of images (ie a scanned magazine) rather than text objects.

Ah, you're correct.  The .pdf was converted from .jpg.  Then I ran pdftk merging all files as a big .pdf.

Having spent an hour unable to find a solution.  Any breakthrough?  TIA

B.R.
satimis

---

### Post by satimis on 2011-05-05
> **Lars Noodén said:**
> Try another PDF viewer like Evince or Okular.

Hi,

Thanks for your advice.

Can they solve my problem?  The pdf was converted from jpg images.

B.R.
satimis

---

### Post by Lars Noodén on 2011-05-05
> **satimis said:**
>  The pdf was converted from jpg images.


Then in that case your data is lost.  You can look around for [OCR](https://help.ubuntu.com/community/OCR) software but you'll still have to proof read and correct it.  OCR tools are far from perfect.

---

### Post by robert shearer on 2011-05-05
If you are going to try the ocr option then this thread may be of help.
Ocr can be configured to perform **very** well, much better than most have come to expect. :)

[http://ubuntuforums.org/showthread.php?t=1714831](http://ubuntuforums.org/showthread.php?t=1714831)

---

### Post by satanselbow on 2011-05-05
There is some good info on the link in the previous post - I suggested gscan2pdf as it works very well for my (not too frequent it must be said) OCR demands. Other solutions obviously do exist :popcorn:

---

### Post by satimis on 2011-05-05
Hi

Thanks for your link

> **Lars Noodén said:**
> 
- snip-

OCR tools are far from perfect.

Agree.  So I think the only solution available for me is;

- running Gimp
- select and copy the text
- paste the same on LibreOffice writer as image
- add my comment on it (below the image pasted)

B.R.
satimis

---

### Post by robert shearer on 2011-05-05
Another ocr option just noticed is...

> Using pdfocr With a Multi Page PDF

pdfocr is a script that uses cuneiform which both performs OCR on multi-page PDF files, and also embeds the text back into the PDF file as a searchable text layer. The script itself can be obtained from Github or from the PPA. To use, simply do:

```
pdfocr -i input.pdf -o output.pdf
```

from the documentation page here...
[https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)

I have not tried this one, though it sounds helpful for your requirement..

---

### Post by ajgreeny on 2011-05-05
There is also a newer version of tesseract than is available from the repos, but can be added from a ppa 
_[https://launchpad.net/~alex-p/+archive/notesalexp](https://launchpad.net/~alex-p/+archive/notesalexp)_
which I am using on 10.04 with very good recognition of text.  It still needs a tiff image to work, but can now be either a tif or tiff, andf it also does now recognise columns.  Give it a try.

---

### Post by satanselbow on 2011-05-05
It does all of course very much depend on the volume or word count you are talking about - might be quicker to cut to the chase and retype it anyway :D

---

### Post by satimis on 2011-05-05
> **robert shearer said:**
> Another ocr option just noticed is...

from the documentation page here...
[https://help.ubuntu.com/community/OCR](https://help.ubuntu.com/community/OCR)

I have not tried this one, though it sounds helpful for your requirement..

Hi,

Thanks for your advice and link.

It serves my purpose even though not 100% perfect.

I followed following link to install the package
[http://ubuntuforums.org/showthread.php?t=1456756](http://ubuntuforums.org/showthread.php?t=1456756)

B.R.
satimis

---

### Post by astrobob.tk on 2011-05-05
> **satimis said:**
> Hi

Thanks for your link



Agree.  So I think the only solution available for me is;

- running Gimp
- select and copy the text
- paste the same on LibreOffice writer as image
- add my comment on it (below the image pasted)

B.R.
satimis


Better yet is let [http://any2djvu.djvuzone.org/](http://any2djvu.djvuzone.org/) do the job of converting ur pdf to djvu & ocr(ing) it. then u can convert it back to pdf if u wish so ;)

P.S.: i personally found ocr in gscan2pdf not that efficient; i still have to test it again.

hope this helps

---

### Post by satimis on 2011-05-05
> **astrobob.tk said:**
> Better yet is let [http://any2djvu.djvuzone.org/](http://any2djvu.djvuzone.org/) do the job of converting ur pdf to djvu & ocr(ing) it. then u can convert it back to pdf if u wish so ;)

P.S.: i personally found ocr in gscan2pdf not that efficient; i still have to test it again.

hope this helps

Hi,

Thanks for your URL.

Unfortunately I can't use their server.  It indicates;```

Extract text from PS/PDF (best for digital documents, not for scanned documents.) 

```

My pdf file contains scanned documents

B.R.
satimis

---

### Post by astrobob.tk on 2011-05-06
> **satimis said:**
> Hi,

Thanks for your URL.

Unfortunately I can't use their server.  It indicates;```

Extract text from PS/PDF (best for digital documents, not for scanned documents.) 

```My pdf file contains scanned documents

B.R.
satimis


Just select the "Scanned Document" (test it, it does a fair job, the least) from [http://any2djvu.djvuzone.org/ulinit.php?submit.x=84&submit.y=16&submit=submit](http://any2djvu.djvuzone.org/ulinit.php?submit.x=84&submit.y=16&submit=submit)
with the appropriate dpi

Notice that on the home page it is stated that

> [FONT=Arial,Helvetica][SIZE=3][SIZE=+1][COLOR=#2c7aa4]You can use the server, for instance, to create DjVu versions of your scanned image documents, to convert your papers in PS/PS.GZ/PDF, or to create multipage "photo-albums" from individual JPEG images. [/COLOR][/SIZE][/SIZE][/FONT]

---

