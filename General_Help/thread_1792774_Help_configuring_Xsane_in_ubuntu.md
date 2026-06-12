---
title: "Help configuring Xsane in ubuntu"
date: 2011-06-28
forum: General Help
---

### Post by Marcus Aurelius on 2011-06-28
I am trying to get my scanner working in ubuntu 11.04.  The scanner is a HP officeJet Pro 8500 wireless a909g.  From ubuntu, I can easily print.  However scanning is another matter.  I am trying to scan to pdf.  I have been trying to use xsane, but when it scans here is what outputs to .pdf.  Imagine a piece of paper on the scanner.  Now divide that paper into vertical columns 1/10th of the actual width of the paper.  The output is one 3/4 of one inch thick vertical column of the intended scanned image.  I am not sure what is causing this.  I was wondering if anyone would help me trouble shoot this problem?

I have only briefly looked into scanner warez for Linux, and am I correct that there is not a whole lot of good applications which will scan an image.... then allow me to crop that image to the correct size, then save that cropped image directly to .pdf?  I think xsane in at least gimp should be able to accomplish this?  

What do you recommend if there is something better?
If this is the best scenario, please advise how I might best troubleshoot the matter so that it scans the entire image, not only a 1/10th vertical strip of the image. 

Thank you very much for reading!

---

### Post by ajgreeny on 2011-06-28
How many separate windows open up when you start xsane, and which ones are they?  There may be a Preview window, but if not Ctrl+1 will show it, and there you may be able to set the area to be scanned.  See screenshot.

---

### Post by Marcus Aurelius on 2011-06-29
> **ajgreeny said:**
> How many separate windows open up when you start xsane, and which ones are they?  There may be a Preview window, but if not Ctrl+1 will show it, and there you may be able to set the area to be scanned.  See screenshot.


In response to your question, here is what happens.  In the attached picture, when I first open xsane (app -> graphics -> xsane) only the middle picture opens all by itself.  Then if I scan an image, a window automatically pops up... see the 3 ring binder holes on the green folder I tried to scan as an image?  See how it only scans that tiny strip?  I think I may have configured this install incorrectly.  Then finally.... you suggested I enter "ctrl+1"... when I do this, the box on the right opens up with no image of the scan inside it.  When I move the mouse around in that preview window, you can see the vertical and horizontal lines that form along that preview windows edges.  That is all that happens.

---

### Post by Marcus Aurelius on 2011-06-30
any ideas as to why the scans come out like this?

---

### Post by smilacq on 2011-11-12
I have exactly the same problems using Xsane. Regularly my "Preview" window gets mixed-up, there is no image and there are no buttons available, thick black lines are created to the top and left side when I move over the panel, appearendly created by the coordinate cursors and I do not know how to get it straight again. Some times I get it working again, but seamingly just by chance. There is a warning on the net ([http://www.yolinux.com/TUTORIALS/LinuxTutorialScanners.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialScanners.html)) about this phenomenon but not an indication how to get out of the problem. Any help is highly appreciated. Does anybody know where to find an extensive tutorial about the use of xsane, not so much about the optical issues but essentialy about the use of the buttons of xsane. Any of he major European languages will do. The scanner works perfect. 
Many thanks
Smilacq

Acer Aspire 7720
Kubutu 11.10
CanoScan 8800F

---

