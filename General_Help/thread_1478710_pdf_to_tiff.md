---
title: "pdf to tiff"
date: 2010-05-10
forum: General Help
---

### Post by noworldorder on 2010-05-10
I am looking for a program that converts pdf files to tiff.  I need this as the VOIP fax program I am using can only fax tiff files.  So if you know of a program that can fax pdf or other document formats that would be even better.

Thanks - chris

---

### Post by finlost on 2010-05-10
The Gimp will import a PDF and export it as a TIFF.  I have no idea on the accuracy of the import and export.  This potential solution seems to be a PITA.

---

### Post by noworldorder on 2010-05-10
Finlost - is that really a picture of you or are you 60 with a pot belly?

---

### Post by noworldorder on 2010-05-10
..

---

### Post by junapp on 2010-05-10
```
convert myfile.pdf myfile.tiff
```

part of ImageMagick.

---

### Post by finlost on 2010-05-11
Girls can get into Linux too ya know. [-(

---

### Post by noworldorder on 2010-05-11
> Girls can get into Linux too ya know.

you have a very nice outfit.

> convert myfile.pdf myfile.tiff

I did this but the tiff file was only one page and blank?

---

### Post by sbergman on 2010-05-11
I worked around this problem a while back (ie: I vaguely remember what to do) by converting the document to a ps format through some command line utilities that you can probably install with apt-get.

tiff2pdf
tiff2ps

pdf2ps
ps2pdf

hmmm... I just realised that there isnt one that converts back to tiff. But since you can use your word processor, where you initially composed the fax to print to pdf and then go from pdf to ps, it shouldnt matter. The above uses GhostScript to work, so apt-get will probably ask you to install that too. Note that sometimes I had to set the version of the output pdf to use by keying in ps2pdf13 or ps2pdf12 (You'll read more in 'man ps2pdf')

Then:

To send ps files as faxes, install efax - you'll end up with 'efax' and it's front-end 'fax', both command line utilities. To send a fax (for example a document doc.ps to a number 55512345) open a terminal, go to the proper folder and type)
fax send 55512345 ./doc.ps

Now I'm not sure it this'll actually send the fax, or simply add it to a fax queue for later processing so there may be another step required... but I'm reasonably sure that it'll work.

---

### Post by noworldorder on 2010-05-11
Thanks [sbergman]("http://ubuntuforums.org/member.php?u=1066677")
I am trying to send a fax via VOIP and found a program that does this but requires tiff files (hense my problem).  Does the fax program you mention send faxes via VOIP?

thanks - chris

---

