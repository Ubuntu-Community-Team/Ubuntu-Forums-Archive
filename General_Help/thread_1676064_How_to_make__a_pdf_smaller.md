---
title: "How to make  a pdf smaller?"
date: 2011-01-26
forum: General Help
---

### Post by christinak on 2011-01-26
Hi all,

this might be a silly question, it might not. I need to send upload some documents (scans) I have onto a website, and there is a limit to how large the pdf can be. (7MB) The file I have - and I can upload only one - is about 10 MB. Is there any command with which I can make this pdf smaller without compromising the resolution too much?

Thank you already in advance!

Cheers,
Christina

---

### Post by LoneWolfJack on 2011-01-26
well, there are only a few things you can do and it looks like you've got them covered.

1. use smaller resolution when scanning
2. convert the images to grayscale (scan in grayscale)
3. compress the pdf files with gzip
4. take a look at the scans, maybe you can crop the images a bit?

5. use imagemagick to force a higher (lossy) compression

```
convert -quality 70 scanned_file.jpeg newfile.jpeg
```

---

### Post by christinak on 2011-01-26
thanks... if all else fails, I will scan the documents I have in grey again. I tried your commandline, but this error

convert: invalid argument for option `-quality': 
oldfile.pdf @ convert.c/ConvertImageCommand/2080.


came up. ?

I also tried what is recommended elsewhere on the web, 

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4 -dPDFSETTINGS=/screen -dNOPAUSE -dQUIET -dBATCH -sOutputFile=output.pdf input.pdf

(here: [http://www.ubuntugeek.com/ubuntu-tiphowto-reduce-adobe-acrobat-file-size-from-command-line.html](http://www.ubuntugeek.com/ubuntu-tiphowto-reduce-adobe-acrobat-file-size-from-command-line.html) if it makes a difference) and that makes it quite small, but the resolution is just horrid.

help?

---

### Post by LoneWolfJack on 2011-01-26
try

```
convert -thumbnail 10000x10000\> -quality 70 scanned_file.jpeg newfile.jpeg
```

note that you can't use this command on pdf files. you need to use it on your scanned images before you put them into the pdf.

---

### Post by christinak on 2011-01-26
Ah... now I see why it is not working :)

The problem is, some (most) of the documents I did not scan myself, but received as .pdf. Hm. With the ones I scanned myself I will definitely try that. Thanks!

---

### Post by christinak on 2011-01-26
ah, once again I solved my own question by reading a little further on the web. 

gs -sDEVICE=pdfwrite -dCompatibilityLevel=1.4  -dNOPAUSE -dQUIET -dBATCH -sOutputFile=newfile.pdf oldfile.pdf 

does the job nicely.

Thanks again, and sorry for asking a question I answered myself :-s

---

### Post by marisdembovskis on 2012-08-20
Worked like charm!
from 4 MB to 178 KB:)
Thanks

---

### Post by wildmanne39 on 2012-08-20
Old thread closed.

---

