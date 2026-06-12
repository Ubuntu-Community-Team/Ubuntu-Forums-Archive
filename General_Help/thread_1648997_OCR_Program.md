---
title: "OCR Program?"
date: 2010-12-19
forum: General Help
---

### Post by ckenpowell on 2010-12-19
New to Ubuntu but believe  graphical OCR capability is limited or non-existent.  If that is so , can one use a Windows OCR program and run it under WINE?  Alternately, can someone suggest a native graphical OCR program for Ubuntu?


Thanks

Ken

---

### Post by karthick87 on 2010-12-19
Welcome to ubuntuforums :)

Check this [**link**]("http://askubuntu.com/questions/16268/whats-the-best-simplest-ocr-solution/16269#16269")

---

### Post by gmargo on 2010-12-19
I just OCR'ed some PDF images recently.  I used the **ocrfeeder** package using **tesseract** as a backend (which is the default if you install ocrfeeder).  It worked well for me.

---

### Post by robert shearer on 2010-12-19
There are several OCR apps for Linux and they work with varying degrees of success.

I have found the **single most important thing** is having a good quality scan (or camera .jpeg) to start with.
 
'scantailor' is helpful in de-skewing and prepping and can be installed from the Ubuntu software center (applications>Ubuntu software center and search for scantailor)  (Gui app)

'tesseract' is a very good app but does not handle multiple columns of text on the same page.  (command line but as noted above ocrfeeder is a gui front-end)

'cuneiform' has been my favoured OCR app. It is command line so you need to run it from the terminal...applications>accessories>terminal.
(such a simple command-line operation that you should give it a try )

Note that the file to be ocr'd needs to be in .bmp format so I open my .jpg with Gimp and then save it as .bmp. (or use your favoured image converter.) and move it to the desktop.

Then in a terminal run...
```
cuneiform -l eng -f text -o /home/[COLOR="Red"]username[/COLOR]/Desktop/[COLOR="Red"]newocr[/COLOR].text /home/[COLOR="Red"]username[/COLOR]/Desktop/[COLOR="Red"]filename[/COLOR].bmp

```
Where the options are...  -l eng =language (use your language)
                          -f =format (there are several options)


html= HTML format
hocr= hOCR HTML format
native= Cuneiform 2000 format
rtf= RTF format
smarttext= plain text with TeX paragraphs
text= plain text

-o = output file (don't forget to make the file format suffix the same as the specified format at -f or you get a > 'PUMA_XSave failed' error. here I have used 'text' as the option and that will output a plain text file.

Replace "username' with your username.
Replace "newocr" with whatever you want to call your ocr file or leave it as is and look for that on the desktop.
Replace "filename" with whatever you saved the original file as.

This should output your OCR conversion in plain text to your desktop.

Links..
[http://manpages.ubuntu.com/manpages/lucid/man1/cuneiform.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/cuneiform.1.html)
[http://www.linuxcertif.com/man/1/cuneiform/330520/](http://www.linuxcertif.com/man/1/cuneiform/330520/)

There is also a .deb package for a **GUI front-end** to cuneiform (lucid) called YAGF that I have used before.
[https://launchpad.net/~ferramroberto/+archive/extra/+build/1773239](https://launchpad.net/~ferramroberto/+archive/extra/+build/1773239)
(when first run change the 'recognition language' to suit. Default is Russian.)

Info for YAGF here...
[http://symmetrica.net/cuneiform-linux/yagf-en.html](http://symmetrica.net/cuneiform-linux/yagf-en.html)

---

