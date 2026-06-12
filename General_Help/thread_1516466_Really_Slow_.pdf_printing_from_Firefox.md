---
title: "Really Slow .pdf printing from Firefox"
date: 2010-06-23
forum: General Help
---

### Post by j0eb0b on 2010-06-23
I am running a dual boot test machine (Windows 7 Professional and Ubuntu 10.04) and have an issue with printing speed of.pdf files on the Ubuntu side.  Both OS instances are 32 bit. I am printing to a Brother 2170 W connected via Ethernet cable to a router.  This evening I downloaded a two page .pdf installation instruction (first page text second 4 pictures in a mosaic).  Firefox was the browser used in both cases.  When printing from the Windows 7 Firefox instance, the text page took about 15 seconds to buffer and load and the graphic page, maybe 30 seconds.  The same test run on Ubuntu/Firefox, the text page took 3-5 minutes to buffer and the graphic page is still loading after about 20 minutes.  

Is this a problem with my Ubuntu Firefox configuration, the configuration on the Brother 2170 W or it's driver or something else?

The print is beautiful when it finally arrives.

thanks,
 Joe

---

### Post by biorancher on 2010-07-07
I had the same problem.  Found the answer here:
[http://ubuntuforums.org/showthread.php?t=1482510&page=2]("http://ubuntuforums.org/showthread.php?t=1482510&page=2")

Basically the printer driver is not very good so you replace it with another one.

Here are the steps:
1. Log on to the cups web interface: [http://localhost:631/admin](http://localhost:631/admin) (for username and pw I used the sudo for this pc).

2. Select "Add Printer"
3. From "Other Network Printers:" I selected: LPD/LPR Host or Printer 
4. under "Connection" put in: socket://IP_of_the_printer:9100 (of course, substitute in the IP of your printer)
5. Name, description, location: fill those out as you wish without spaces
6. Sharing: I did not check this box.
7. Make: Select Generic and click Continue
8. Model: Generic PCL 5e Printer Foomatic/hpijs-pcl5e (recommended)
(this model is the closest by name to what Johnny_vc told me to use. I figured mine is different because I'm using Lucid) 
9. Click "Add Printer" and you're done.

---

### Post by gnipper on 2010-07-15
I think the answer is in turning off 'share printer'. Printing PDF's was really slow for me on two different network printers until I turned off 'share printer' in system-config-printer. I'm running Xubuntu 10.04 64 bit.

---

