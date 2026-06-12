---
title: "Tesseract and xsane2tess with 10.10"
date: 2010-11-04
forum: General Help
---

### Post by Sigma1 on 2010-11-04
Hello,
I used to be able to use Tesseract with a nice script called xsane2tess to feed .tif files directly from xsane into Tesseract for OCR conversion into text files. This worked under 8.04 and 10.04, but no longer seems to function using 10.10. I originally installed xsane2tess via [http://doc.ubuntu-fr.org/xsane2tess](http://doc.ubuntu-fr.org/xsane2tess) (French site and documentation).
The problem, I think, must concern the script in 10.10, since, when I run Tesseract on a .tif file from the command line, I get no errors and the OCR works fine. Has anyone else had any similar problems, and if so, are there any workarounds or tweaks of the script available to make OCR easier?
Thanks in advance for any help!

---

### Post by Sigma1 on 2010-11-06
Not a solution, but a workaround, found on a French website (here [http://www.equinoxefr.org/post/2008/07/05/xsane-et-tesseract-locr-qui-marche-tres-bien-sous-linux/](http://www.equinoxefr.org/post/2008/07/05/xsane-et-tesseract-locr-qui-marche-tres-bien-sous-linux/)), using a perl script to do the same job as xsane2tess. It works for me, in 300, 600 or 1200 dpi, at least (tested).

```
cd /usr/bin #changes to the right directory
sudo wget http://www.equinoxefr.org/wp-content/uploads/2008/07/xsane2tess.pl #downloads the perl script into /usr/bin/
sudo chmod +x xsane2tess.pl #renders the script executable
```

Then you launch xsane, and, provided you have tesseract-ocr, the right language files for your language, and imagemagick installed, you go to Preferences/Configuration and enter the following, in the OCR tab: 
OCR Command: xsane2tess.pl -l fra -log /tmp/tesseract.log
[This tells xsane 1. to use the new, perl script, 2. which language recognition data to use, replace "-l fra" with "-l eng" for English, of course, and 3. to keep a log in /tmp/.]
Input options: -i
Output options: -o
Graphic interface: -x
The last box is left empty.
Hope this helps somebody!

---

### Post by hvf on 2010-11-24
After struggling to get the bash script working for a few hours, I found this solution - works like a charm! Thanks

---

