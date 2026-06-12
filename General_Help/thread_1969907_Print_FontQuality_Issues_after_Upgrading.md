---
title: "Print Font/Quality Issues after Upgrading"
date: 2012-04-30
forum: General Help
---

### Post by magwhyte on 2012-04-30
Thanks in advance for any assistance.

I have upgraded on both my work and home desktops to 12.04 and am very happy with it.  However, when printing I get a very low quality output.  It looks like it was printed circa 1985 with a cheap dot matrix printer.  This is happening with all types of documents (e.g. .doc, .pdf, etc.).

Has anyone else had this problem and if so, what were you able to do to resolve it?

Again, many thanks for any assistance.

---

### Post by nexx on 2012-05-03
Same printing problem here and also very happy with Ubuntu 12.04. After upgrading to Ubuntu 12.04 with my T43 Thinkpad IBM Laptop, if I print a pdf document formatted with Ubuntu fonts, the printed output is way lower quality that the same document printed with Ubuntu 11.10

Tried finding a font package in the app store but with no avail.:confused:

---

### Post by chaarmann on 2012-05-03
The same with me: After upgrading Ubuntu to 12.04 from 11.10, printing a PDF gives a very poor quality printout.I have an HP Color Laserjet 2600n.

Workaround: I opened the PDF with Gimp. When I choose the default (100 pixels per inch) I get exactly the same poor printout as if printing from document viewer.
But if I choose 600 pixels per inch, I get a high quality printout, as it was before upgrading Ubuntu.

So I guess the error is that somehow the document viewer chooses the default 100 pixels per inch instead of using the maximum possible for the printer. If so, then the question is, where can I configure the print quality of the document viewer?

---

### Post by Wim Feijen on 2012-05-06
Hi, I am experiencing the same issue.

When I look into the printer settings, printer quality is still set to normal.

I am using a HP Color Laserjet CP1215.

---

### Post by magwhyte on 2012-05-12
Help?

---

### Post by dewmax on 2012-05-14
Same issue on a HP printer after upgrade to 12.04...

---

### Post by chaarmann on 2012-05-19
I finally solved the problem!!!
It's the printer driver that has changed when upgrading Ubuntu from version 11.10 to 12.04.

Solution:
I first went to the Ubuntu software center and installed  "HPLIP-Toolbox"and ran it. It detected my printer and also tried to  automatically download and install the needed driver from internet. The  first time I tried it, it gave me an error when downloading the driver.  So I executed "sudo hp-setup" in a terminal and the driver was  downloaded and installed successful.

Verification:
I opened "Printing" from the dash and there should be 2 printers now  with the same name. I opened the first and saw that this was the old one  with a "Make and Model"= "foo...". The second had "hpijs 3.12.2  requires proprietary driver" instead. So I set the second as default  printer and deleted the first one.

Now printing from Libre Office, Firefox or PDF has the same high quality as before I upgraded the ubuntu version.
I even noticed a better quality when printing black parts of an image  (not text! Text was always fine): Before the black was rather grey and  looked like "draft", but now I have a saturated deep black instead.

---

### Post by nexx on 2012-05-19
Thanks chaarmann, worked like a charm. :popcorn:

---

