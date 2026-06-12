---
title: "Scan to PDF"
date: 2012-03-17
forum: General Help
---

### Post by ddjolley on 2012-03-17
I know that many of the high-end copiers have the capability of copying to a PDF and then emailing the PDF to an email address.  That would be great; but, that requires a high-end copier which I don't have (and won't be getting).  What's the next best thing?  I'm running Ubuntu 11.10 on my desktop.  I have a compelling need to be able to scan documents into a PDF.  What hardware/software do I need to achieve this goal?  Thanks for any input.

         ... doug

---

### Post by Cheesehead on 2012-03-17
Any scanner that works with SimpleScan (included in the default install).

SimpleScan will save as PDF.

---

### Post by ajgreeny on 2012-03-17
Scan it as an image then simply print the image by using "Print to file" instead of the normal printer.  You should then have the option of printing as a .ps or as a PDF.

Silly me!  I did not think about simple-scan or xsane, both of which will do that.

So now we know there are three ways!

---

### Post by wallaroo on 2012-03-17
Another good program is 'gscan2pdf' (available via Software Manager), it provides many more options than 'Simple-Scan', including many output formats and several page 'clean-up' and OCR options.

---

### Post by jquis8411 on 2012-03-17
I scan to PDF all day using X-Sane f

---

### Post by raja.genupula on 2012-03-18
[http://www.ubuntugeek.com/scan-to-pdf-using-gscan2pdf-in-ubuntu.html](http://www.ubuntugeek.com/scan-to-pdf-using-gscan2pdf-in-ubuntu.html)

---

### Post by villalcalde84 on 2012-03-18
I think simple scan is the best option to try, as it is  installed by default in Ubuntu 11.10. If not enough for you, try other options as suggested by other users.

---

### Post by ddjolley on 2012-03-18
Thanks for all the helpful info.  I had SimpleScan working (over the network even) with our HP 6310 network-based All-In-One in minutes.  Since SimpleScan is installed by default, I didn't even have to install anything!  That's a real confidence builder and it let's me know that I have compatible hardware.  Now I can move on to trying the more advanced solutions.  Thanks to all who contributed.

        ...doug

---

### Post by johan_olsen on 2012-04-01
Hi!
I have a Canon Pixma MP560 which has been working perfectly until last week. The printing is ok, but there has come a scanner problem. The result is the same in SimpleScan and XSane - the scanned document shows a randomly placed grayish fields,(the original on the attatchemt is a white paper with no shades) see the attachment. If I scan to a USB inserted in the printer, the result is fine, so the problem is not in the printer. I connect to the printer wireles and uses Ubuntu 11.04 - I hope sombody out there can help me find out what is wrong!

Johan, Norway.

---

### Post by raja.genupula on 2012-04-01
Its always better to start a new thread for getting much better Help . so please start a new thread for your issue .

---

### Post by johan_olsen on 2012-04-01
> **raja.genupula said:**
> Its always better to start a new thread for getting much better Help . so please start a new thread for your issue .

Thanks, I should have known :-)

---

### Post by HiImTye on 2012-04-02
```
sudo apt-get install imagemagick
```
save them as .png and then just batch convert them
```
convert *.png *.pdf
```

---

### Post by HiImTye on 2012-04-02
@Johan,
use The GIMP to scan, I find that it works best with my canon wireless MP495

---

