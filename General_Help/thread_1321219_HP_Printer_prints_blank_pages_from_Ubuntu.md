---
title: "HP Printer prints blank pages from Ubuntu"
date: 2009-11-09
forum: General Help
---

### Post by lorderico on 2009-11-09
Hello,

I have an HP Deskjet 3845 printer.  I had new cartridges in my printer, and it printed fine for a while.  Then Ubuntu started telling me that the printer is low on ink, and the printer stopped printing ink (just white paper).  I replaced the cartridge with a new one, and I got about 4 pages with black ink before it stopped printing ink again.  My Windows computer will print on the printer, but the pages come out grey (as if it is losing ink).  I would love it Ubuntu would at least print grey, instead of printing blank when there is clearly ink left.  Do you have any suggestions that I could try to fix/further diagnose this problem?

Thanks,
Eric

---

### Post by Madel on 2009-12-06
Same problem.

Printer works fine in window$ but print nothing in Ubuntu 9.10.

Printer looks like it's printing, with the ink cartridge going side ways back and forth as if it's printing. But nothing gets printed. Just blank.

Printer im using is HP Deskjet 3745.

---

### Post by Ryann on 2009-12-06
Ditto on HP 5600. (No message about low ink, it looks as if it will print without a problem but then a blank page is spit out).

---

### Post by kentechy on 2009-12-06
My advice would be to get "TurboPrint".  It manages Ubuntu printing very well.  After experiencing lots of problems I got TurboPrint and it fixed everything.  Here is a link.  [http://www.turboprint.info/](http://www.turboprint.info/)

---

### Post by bumanie on 2009-12-06
I would go [here]("http://hplipopensource.com/hplip-web/index.html") and reinstall the printer divers from HP for linux. Download the driver and then go to 'more information' and follow the installation instructions. I have had the ubuntu driver not work right once or twice, but the driver off the HP site has never failed.

---

### Post by Madel on 2009-12-07
> **bumanie said:**
> I would go [here]("http://hplipopensource.com/hplip-web/index.html") and reinstall the printer divers from HP for linux. Download the driver and then go to 'more information' and follow the installation instructions. I have had the ubuntu driver not work right once or twice, but the driver off the HP site has never failed.

does that mean i have to download the HP driver from HP website? it's something like auto installer from what i understand. but, is it safe to do so? or do i have to unintall the HLIP built in ubuntu before installing the new driver from HP website?

---

### Post by hieppo000 on 2009-12-24
mine does the same HP PSC 2410.  I downloaded and installed hplip.  still does not print from any text editor or open office.  I also tried using greyscale doesnt work.

what did work for me...was exporting to PDF and then printing the PDF file.  it really blows goats to do this.  but it was the temp fix for me.

---

