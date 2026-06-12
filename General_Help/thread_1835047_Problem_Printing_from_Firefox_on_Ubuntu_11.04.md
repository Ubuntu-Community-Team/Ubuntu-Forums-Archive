---
title: "Problem Printing from Firefox on Ubuntu 11.04"
date: 2011-08-28
forum: General Help
---

### Post by jonbjoseph on 2011-08-28
Whenever I submit a print request from Firefox, the print request is added to the printing queue for the selected printer (HP-LaserJet-1200),but never prints.  I just tried to print a simple page (google.com) from Firefox and waited over 10 minutes and nothing was printed.  I've waited as long as 20 minutes after submitting a print request from Firefox and nothing was printed.

I'm able to print from other applications such as LibreOffice or gedit. 
Note, I can print from Google Chrome, but have to wait a few minutes for a simple web page to print.

Can anyone provide me with some tips on how to diagnose, fix this problem?

Thanks,
Jonathan

---

### Post by soumyabratapaul on 2011-08-28
Try to take a test page print, form your printer. If this fails, which I think will, just disconnect all the cables of your printer from your computer, and then delete all the settings of your printer. Then after doing this, just connect your printer cables, and then turn your printer on. Then after doing this, you will be prompted, that a new device have been connected. Set your printer, now, via the automated, wizard, and download all the necessary drivers(proprietary ones, cause the open-source ones will be automatically downloaded, if you have set them to do so). See now, if it helps.

---

### Post by jonbjoseph on 2011-08-28
> **soumyabratapaul said:**
> Try to take a test page print, form your printer. If this fails, which I think will, just disconnect all the cables of your printer from your computer, and then delete all the settings of your printer. Then after doing this, just connect your printer cables, and then turn your printer on. Then after doing this, you will be prompted, that a new device have been connected. Set your printer, now, via the automated, wizard, and download all the necessary drivers(proprietary ones, cause the open-source ones will be automatically downloaded, if you have set them to do so). See now, if it helps.

But why is the problem unique to Firefox?  That's what I can't figure out.  All other programs can print.

---

### Post by timpire on 2011-09-29
I am facing the same problem as jonbjoseph but i am using Samsung ML2010 laser printer. The printer works properly except when i need to print something from firefox web browser

Besides, I've tried to print with Opera, the webpage has 5 pages long, so i put my printer settings as:
Page: 1 - 2
Copies: 1

As the result, it printed  5 pages x 2 times.

Any solution for this?

---

### Post by timpire on 2011-09-29
Jonathan, i have fixed my firefox printing problem. For your reference, this is what i've done. I changed my Printer Option to:

Manual Feed of Paper : Off
Economy Mode : Off
Halftoning Algorithm: Standard

These are the changes that i've made, now my firefox can print properly.
Hope this will help :)

---

