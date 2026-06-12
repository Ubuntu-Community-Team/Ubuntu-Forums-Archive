---
title: "CUPS &amp; Printer Alignment"
date: 2009-11-13
forum: General Help
---

### Post by zzzBrett on 2009-11-13
I have a Brother HL-2140 that is not properly aligned. I have searched and can't find a clear option or setting that I change in order to properly align the printer / CUPS driver.

Anyone know how to do this?

---

### Post by zzzBrett on 2009-11-15
bump

---

### Post by zzzBrett on 2009-12-07
bump

---

### Post by zzzBrett on 2010-01-05
anyone?

---

### Post by zzzBrett on 2010-01-09
bump

---

### Post by lyall on 2010-01-09
see the following link for info about your printer

[http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2140]("http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2140")

It states the driver you should use

good luck and have fun learning

---

### Post by zzzBrett on 2010-01-09
> **lyall said:**
> see the following link for info about your printer

[http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2140]("http://www.openprinting.org/show_printer.cgi?recnum=Brother-HL-2140")

It states the driver you should use

good luck and have fun learning

This doesn't say anything about alignment.

---

### Post by zzzBrett on 2010-01-09
Finally may have found an answer!

> 6. 	Adjust the print margins.

(If you are not using Foomatic or if the margins on your printouts are correct, skip this step). Download the files align.ps and alignmargins, then run alignmargins as root and follow the instructions:

cd /tmp
wget [http://www.openprinting.org/download/printing/align.ps](http://www.openprinting.org/download/printing/align.ps)
wget [http://www.openprinting.org/download/printing/alignmargins](http://www.openprinting.org/download/printing/alignmargins)
chmod 755 alignmargins

su
./alignmargins

   OR

sudo alignmargins

This will add the Margins print option so you can turn on ("lpr -o Margins=Custom printfile", default setting) or off ("lpr -o Margins=Default printfile") your adjustments.
Note that this does not work for all drivers. 

[http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/cupsdocumentation](http://www.linuxfoundation.org/collaborate/workgroups/openprinting/database/cupsdocumentation)

---

### Post by lyall on 2010-01-09
glad you found the fix, good work

some times we all have to search around and read to find the answer

good luck and have fun learning

---

### Post by zzzBrett on 2010-01-10
> **lyall said:**
> glad you found the fix, good work

some times we all have to search around and read to find the answer

good luck and have fun learning

Trust me, i've been searching for a while :)
But yes, I found the 'fix', but it doesn't seem to be working for me really. I'll have to play around with it this week.

---

