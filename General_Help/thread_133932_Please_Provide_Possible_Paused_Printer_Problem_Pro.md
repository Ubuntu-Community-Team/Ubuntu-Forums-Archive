---
title: "Please Provide Possible Paused Printer Problem Proposals"
date: 2006-02-21
forum: General Help
---

### Post by spookygeek on 2006-02-21
My Printer will not print.  It detected/installed fine, and can be viewed from system->Administration->Printing.  However when I try to print The Printer does nothing, and instead it pauses the printer.  (printer is HP 3320) I notice that under the "status" field on the printer properties the following text is listed.

Paused: Unable to open USB device "usb://hp/deskjet%203320?serial=LPDTESTLD": No such device

Any help on this, I'd love to be able to print one day.

Thanks again to whoever can help.

-Brent

---

### Post by Madpilot on 2006-02-21
First of all, bonus points for your topic title's amazing alliteration! :P

[https://wiki.ubuntu.com/HardwareSupportComponentsPrinters](https://wiki.ubuntu.com/HardwareSupportComponentsPrinters) has your printer mentioned, with the comment "Not detected. Have to choose it from the list in Gnome printer install." but listed as working...

Check linuxprinting.org, too. A quick search there found:
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_3320_MFP](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_3320_MFP)
and
[http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_3320N_MFP](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_3320N_MFP)
... have a look at the tips there on getting your printer working.

At least it's an HP, they're good with Linux usually...

---

### Post by spookygeek on 2006-02-24
Bump

---

### Post by Zimmer on 2006-02-24
Check Synaptic for the following packages, which may help with an HP printer..see if they are installed..

hpijs
foomatic-db-hpijs
hplip-base
hplip-ppds

Also, which applications have you tried printing from?
The Gimp has a particularly interesting way of setting up the printer, and I had  to have a good few reads of the help file before I got it right.
(I have an HP 930 series, BTW , which works fine..)

---

### Post by spookygeek on 2006-02-25
Everything checks out yet no printing, I got a feeling it might be a permission problem, but I've no idea where to start.  There are a ton of other threads with similar issues, I hope whatever is causing this is fixed in Dapper.

Thanks,

-Brent

---

### Post by spookygeek on 2006-02-25
Paused: Unable to open USB device "usb://hp/deskjet%203320?serial=LPDTESTLD": No such device

Thats the info listed under "system" when i open my printers properties when it won't print and instead just pauses.

Any ideas?

Thanks,

-Brent

---

### Post by Zimmer on 2006-02-25
[http://www.thisishull.net/showthread.php?t=61061&goto=nextnewest](http://www.thisishull.net/showthread.php?t=61061&goto=nextnewest)

found this for you, the replies suggest creating a rule for udev for the printer, but no firm reply is there  as to success....
The documentation for that is at 
usr/doc/udev.

---

### Post by astoltz on 2006-02-25
I have an HP 3650 that did the same thing once.  I fixed it by just removing the printer and adding a new one in the printer configuration.  Open up System -> Administration -> Printing and add a new printer.  In the "step 1" dialog, pick Local Printer and pick "Use another printer by specifing a port".  Then from the Printer Port List, pick USB Printer #1 and click forward.  In step two, pick your printer from the list and keep the default driver. Click apply and hope it works...

---

### Post by spookygeek on 2006-02-28
No luck yet, any one esle have ideas?

-Brent

---

### Post by tinker312 on 2006-02-28
Hi, 

Get a new printer! J/K

Yours . . . 
John

---

### Post by DrSkalpell on 2006-03-01
I also have this problem with my Canon i350 using turboprint-drivers.

Worked perfect until one month ago. Suddenly I got:

paused: Unable to open USB device "usb://Canon/i350": No such device

Could it have something to do with updated packages?

---

### Post by DrSkalpell on 2006-03-20
I solved the problem by reinstalling cups

---

