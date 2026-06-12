---
title: "Help withXerox Phaser 3200mp scanner/copier/printer"
date: 2012-04-09
forum: General Help
---

### Post by Biciclettapc on 2012-04-09
11.04

System see's the printer and install fine. I generate a test file and printing to file(pdf) works perfect.

A self test from the print driver gives me what it should.

But, if i send a job (test from librewriter) I get ascii gibberish for pages.

Help

TIA
Paul

---

### Post by searchfgold6789 on 2012-04-09
Try rebooting, or restarting cups: ```
sudo restart cups
```If all else fails, try uninstalling and then reinstalling the printer. You can find a PPD file and other info here: [http://www.openprinting.org/printer/Xerox/Xerox-Phaser_3200MFP](http://www.openprinting.org/printer/Xerox/Xerox-Phaser_3200MFP)

---

### Post by Biciclettapc on 2012-04-10
> **searchfgold6789 said:**
> Try rebooting, or restarting cups: ```
sudo restart cups
```If all else fails, try uninstalling and then reinstalling the printer. You can find a PPD file and other info here: [http://www.openprinting.org/printer/Xerox/Xerox-Phaser_3200MFP](http://www.openprinting.org/printer/Xerox/Xerox-Phaser_3200MFP)

Thanks, I will try resetting the cups.

I did uninstall and then reinstall the printer with no luck.

This is on my neighbors system that I built for them, the printer was a old work printer they had laying around.  So it will be this evening before I can try the reset.

Paul

---

### Post by Biciclettapc on 2012-04-10
> **searchfgold6789 said:**
> Try rebooting, or restarting cups: ```
sudo restart cups
```If all else fails, try uninstalling and then reinstalling the printer. You can find a PPD file and other info here: [http://www.openprinting.org/printer/Xerox/Xerox-Phaser_3200MFP](http://www.openprinting.org/printer/Xerox/Xerox-Phaser_3200MFP)

No luck with restarting cups.

How do deal with ppd files?

Thanks
Paul

---

