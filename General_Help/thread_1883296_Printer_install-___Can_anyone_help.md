---
title: "Printer install-   Can anyone help"
date: 2011-11-18
forum: General Help
---

### Post by pafire on 2011-11-18
I'm trying to install a Panasonic kx-p1124 printer in Ubuntu 10.04. I have tried to install it via the system/admin/printing/add a printer. The data base suplied a printer driver that did not work.  That resulted with the printer printing garbage and leaving the print jobs in grenblin land. After deleting the printer and rebooting several the print jobs still accumilite. I guess the first step would be to delete the print jobs. How can I do this step?? Does anyone have a good working driver or a posibbly a guide to install this printer.

---

### Post by L a r r y on 2011-11-18
> **pafire said:**
> I'm trying to install a Panasonic kx-p1124 printer in Ubuntu 10.04. I have tried to install it via the system/admin/printing/add a printer. The data base suplied a printer driver that did not work.  That resulted with the printer printing garbage and leaving the print jobs in grenblin land. After deleting the printer and rebooting several the print jobs still accumilite. I guess the first step would be to delete the print jobs. How can I do this step?? Does anyone have a good working driver or a posibbly a guide to install this printer.
I am not sure I can help, as I have the Photosmart 1115 by HP on my 10.04, and I go to 
> System > Administration > Printing
and from there right-click on the printer's icon and then the bottom menu item lets me view print jobs.  Job menu on that screen lets me cancel.

Having blown all that away, it would be nice to know where in the file system one needs to go to manually delete the print jobs, or I wonder if you reinstalled the printer, it would let you follow my instructions and cancel them?

IIf you have not already done a Google search, I found this document that may be of value.  I am still trying to find where print jobs are keopt, so I will do some reading myself:

> [https://help.ubuntu.com/8.04/printing/C/printing.html](https://help.ubuntu.com/8.04/printing/C/printing.html)

Couple years old (8.04) but may still apply to 10.04.

Larry

---

### Post by L a r r y on 2011-11-18
I found a man page about the:
> [URL="http://manpages.ubuntu.com/manpages/maverick/man5/lpd.conf.5.html"]lpd.conf - configuration file for the LPRng line printer spooler system
[/URL]
that may have more information for you.

---

### Post by Miljet on 2011-11-18
I don't know about the printer driver, but the easiest way to cancel all print jobs is to open a terminal and enter ```
sudo cancel -a
```

That will kill all pending print jobs. You can also kill jobs for a particular user, printer, etc. See "man cancel" for details.

---

### Post by pafire on 2011-11-20
After many attempts to add a panasonic kx-p1124 printer I'm recieving the following message. Test page submitted as job 19. How can I delete these printing jobs in Ubuntu 10.04 lts.

---

### Post by SoFl W on 2011-11-20
The 1124?  Isn't that an old 24pin dot matrix printer?  Great printer... I had it 20 years ago.  

See this thread
[http://208.109.22.214/puppy/viewtopic.php?t=46003&sid=f59269a0fdf053d2b9e5cd1e941da51c](http://208.109.22.214/puppy/viewtopic.php?t=46003&sid=f59269a0fdf053d2b9e5cd1e941da51c)

---

### Post by pafire on 2011-11-20
SoFl W - you are correct, it is a 24pin dot matrix printer

---

### Post by pafire on 2011-11-20
SoFl W - thanks for the redirect, however the site is down for maintence. do you have any ideas as to how I can delete those print job numbers. I'm up to 19 and still climbing.:confused:

---

### Post by JKyleOKC on 2011-11-20
The directory at /var/spool/cups has a number of files with numbers in their names, each of which **may** be a job in the print queue. The files include binary data so cannot be viewed with a normal text editor; I used the terminal command "hexdump" to examine them and they certainly appear to be leftover jobs that no longer show up in my printer status displays. This directory is readable only by its owner, which is "root" so you need to use gksudo to launch your file manager if you want to view it.

I have no idea what would happen if you deleted these files, and am not willing to try it on my main system. I just got the networked printers working properly, after more than a year of trial and error. The files I see there are all left over from such errors, so far as I can tell...

---

