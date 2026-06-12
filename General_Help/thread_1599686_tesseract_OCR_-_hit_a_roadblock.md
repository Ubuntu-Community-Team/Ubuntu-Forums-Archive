---
title: "tesseract OCR - hit a roadblock"
date: 2010-10-18
forum: General Help
---

### Post by TheSiberian on 2010-10-18
I have been trying to get tesseract OCR going, but have hit a point at which I can go no further.

I ran a simple command, such as:
```
tesseract infile.tif output
```The command runs without error, but the output.txt file is just a single byte file. 

In order to rule out an issue with the tif file - I used some example files found on the [tesseract issues page]("http://code.google.com/p/tesseract-ocr/issues/list")

I have been scouring the web for some manuals/example, but cannot find anything thorough.

Any help/guidance is appreciated!

- additional minor question, the values for -l (langid) are eng, deu, (etc..) right? or is there an actual numeric value?

---

### Post by TheSiberian on 2010-10-18
Just to add a little further, I issued the following:
```
tesseract myfile.tif output > teslog.txt &> teserror.txt
```The teslog.txt file was empty.

The teserror.txt file contained:  **Tesseract Open Source OCR Engine**

---

### Post by TheSiberian on 2010-10-21
anyone? not sure where to go from here..

---

### Post by oregonbob on 2010-10-21
> **TheSiberian said:**
> Just to add a little further, I issued the following:
```
tesseract myfile.tif output > teslog.txt &> teserror.txt
```The teslog.txt file was empty.

The teserror.txt file contained:  **Tesseract Open Source OCR Engine**

You specify an output file, but you also try to redirect output. I don't know the command line format and options but that doesn't look right. If you want to redirect standard error messages try this:

tesseract myfile.tif output 2> teslog.txt

Maybe tesseract uses convention so try this:

tesseract < myfile.tif > output

It would be nice to see a 'man' page for tesseract.

---

### Post by perspectoff on 2010-10-21
Does Ocropus make things any easier?

(Ocropus is Google's user envelope for Tesseract).

Install Ocropus:

 sudo apt-get install ocropus

---

### Post by TheSiberian on 2010-10-22
> **oregonbob said:**
> You specify an output file, but you also try to redirect output.
my intention for that command was to:

> tessog.txt: direct standard output (STDOUT) to a file
&> tesserr.txt: direct any errors (STDERR) to an error file.

this was done after reading some help on redirecting output.. so maybe I need to read it again........


I will have a look at ocropus & feed back again.

---

### Post by Sigma1 on 2010-11-04
Hello,
Do you have the language files for tesseract installed too? Empty files sometimes happen when tesseract can't find the language files it needs. You should have a tessdata file next to tesseract in /usr/bin.

---

### Post by tkoco on 2010-12-12
Usage is simple. I use it like this:
```
tesseract test6.tif test-tif-6
```

And the resulting file is "test-tif-6.txt" in the same directory as the image file. No redirects needed. The input image file is typically scanned in at 1200 pixels per inch as a "Line Art" type.

---

