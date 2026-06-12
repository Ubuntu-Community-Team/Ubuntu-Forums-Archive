---
title: "HP printer working very slowly"
date: 2011-04-04
forum: General Help
---

### Post by crogers on 2011-04-04
I have  an HP LaserJet 1200 printer and Ubuntu 10.10. The printer has recently started working very slowly or not at all for PDF files.

I used Ubuntu Software Center to download HPLIP version 3.10.6-1ubuntu10.2 (hplip-gui).  Then  used CUPS and HPLIP to uninstall and re-install the printer. No Change in performance.

Open Office Applications seem to print OK.  Firefox can print web  pages that have no graphics.  Small PDF files with no graphics will come out eventually.   Larger, more complex PDF files get stuck "processing." 

The printer hardware is OK. The issue  is either my recently upgraded Ubuntu or the CUPS configuration or the  HPLIP configuration. I'm not enough of a LINUX guru to take it much farther.

Web searches reveal other users apparently having  similar symptoms. 

Any suggestions of what to try next?

Thanks for the help!

In the absence of any responses, I'll, none the less, in the interest of anyone who may find this in a search for a fix to a similar problem, provide an update:  

:pThis problem was resolved by the following.

I observed that CUPS listed two HP 1200 printers as available.  I used the CUPS GUI dialog to delete one.  Apparently I had a 50% chance of deleting the correct one and I got lucky.The correct driver that I should have selected is the "foomatic" (recommended) driver.  Now my functionality is restored.

---

