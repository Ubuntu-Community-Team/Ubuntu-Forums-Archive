---
title: "Printer, All Jobs Held"
date: 2009-06-29
forum: General Help
---

### Post by ftabor on 2009-06-29
Suddenly, all my print jobs are being "Held Until Evening" in the "Documents Print Status" box and I have to manually release them.  This ain't good.  Something has changed this recently and I don't know why.  I can't find anything in any of the printer properties.

I'm using a network printer attached to a hub, (home network) and it has been running fine.  I think I saw a cups system update in the last day or two but I can't be sure.

I ran the troubleshooter, and the first line of the file is, "scheduler not running".  The troubleshooting file is attached.  

I know zero about the cups system, other than it works automagically, when it works.  Thanks for any assistance.

Edit: Well, after hours of searching, I finally found in the /etc/cups/printers.conf the line "Option job-hold-until evening".  I commented it out and restarted cups, and now all is well.  This option does not appear in the printer property settings anywhere.  As near as I can tell, it's a command line option one can set to control print times.  I can find nowhere in any of the printer dialogue boxes to set this option.

---

### Post by dsiddens on 2010-01-07
Helo ftaber,

Under Ubuntu 9.10

If you open System>Adminstration>Printing.  
Double click your printer, select Job Options, then under Common Options hit >More. 
Select from "Hold until" what you want.

Doug

---

### Post by ftabor on 2010-01-07
If you would reread my post, you'll see that what you posted was not my problem, and I marked the problem solved 6 months ago with the proper solution.

---

### Post by audiomick on 2010-01-07
But dsiddens did explain a GUI solution for this
> As near as I can tell, it's a command line option one can set to control print times. I can find nowhere in any of the printer dialogue boxes to set this option.
There is also a "no hold" option there, which would make the same change to /etc/cups/printers.conf that you made by editing, I would think ;)

---

### Post by ftabor on 2010-01-07
If I remember correctly, this was set to "No Hold".  In the conf file it was set to Evening and no amount of resetting the options would change it.  I ended up having to edit the file manually to change it.

---

