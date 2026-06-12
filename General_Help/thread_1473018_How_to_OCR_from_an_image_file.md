---
title: "How to OCR from an image file?"
date: 2010-05-04
forum: General Help
---

### Post by HiSiskin on 2010-05-04
I have an image file which has a text captured on it:

[http://homepage1.nifty.com/algafield/microsofthumor.jpg](http://homepage1.nifty.com/algafield/microsofthumor.jpg)

How could I get a plain text file from this? Does Ubuntu have a software for that?

Thanks in advance!

---

### Post by foxmulder881 on 2010-05-04
It's not possible. Image files and text files are completely different and are read by your computer in completely different ways.

If you're keen, you could retype it up into a text file!

---

### Post by Marlonsm on 2010-05-04
I think gocr can do it, but IIRC it's command-line based;

Open the terminal.

Install:
```
sudo apt-get install gocr
```

save the image to some directory (saving it in Home is easier, as the terminal defaults there)
and run:
```
gocr <file name>
```

if you need to change the directory the terminal is in, use:
```
cd Desktop
```
if you want to go to the desktop, for example.

You can also check the software centre for graphical alternatives.

BTW, most ocr softwares will convert files to a text-only format, so you'll lose that table format.

---

### Post by HiSiskin on 2010-05-04
Thanks Marlonsm for your help.
The gocr program did the trick.
I think the inaccuracies of the result may be minimized by preprocessing the original image using GIMP.

Thanks again.
Ubuntu and its community are great!

---

### Post by junapp on 2010-05-04
recent copy of full circle magazine mention [http://gscan2pdf.sourceforge.net/](http://gscan2pdf.sourceforge.net/) as a good option, although I believe the part you need is really just something like you've got with gocr, but you may find tesseract to provide better results.  see: [http://code.google.com/p/tesseract-ocr/](http://code.google.com/p/tesseract-ocr/) or see tesseract-ocr in the repositories.

---

### Post by foxmulder881 on 2010-05-06
My apologies if I put the OP on a bum-steer with my first reply. I completely misread the original post and completely misunderstood what you were trying to achieve. So yeah, apologies mate.

---

