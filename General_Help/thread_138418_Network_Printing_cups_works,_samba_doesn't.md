---
title: "Network Printing: cups works, samba doesn't"
date: 2006-03-01
forum: General Help
---

### Post by pyromaneyakk on 2006-03-01
I've been trying for the past 2 days to get network printing to work.  This is starting to drive me mad!  I just got a Samsung ML-2010 printer.  I have installed the printer drivers that came with the printer and printing from the server, as well as my notebook running Dapper Drake 6.04 works flawlessly.  It is when the windows machines on my network try to print when I come into problems.  I have tried both the MS postscript driver and the CUPS binary driver to no avail.  When I try to print, I get the following message in the CUPS error log:

```
I [01/Mar/2006:21:34:03 -0500] Job 27 queued on 'lp' by 'Kyle'.
I [01/Mar/2006:21:34:03 -0500] Started filter /usr/lib/cups/filter/pstops (PID 22330) for job 27.
I [01/Mar/2006:21:34:03 -0500] Started filter /usr/lib/cups/filter/ppmtospl2 (PID 22331) for job 27.
I [01/Mar/2006:21:34:03 -0500] Started backend /usr/lib/cups/backend/usb (PID 22332) for job 27.
E [01/Mar/2006:21:34:03 -0500] [Job 27] Failed to load the PPM image
E [01/Mar/2006:21:34:03 -0500] PID 22331 stopped with status 3!
```

I have also tried using the Samsung 4500 driver.  Again, printing from linux remotely or locally works great.  When I try printing over SMB though, instead of getting an error in the CUPS log, I get the following page printed:

```
ERROR: undefinedresult
OFFENDING COMMAND: itransform

STACK:

6250.25
-119.75
/TextInit
-mark-
```

Perhaps someone has some insight on this problem?  Maybe i'm missing something...  thanks in advance!

---

### Post by shanepardue on 2006-10-16
i can't seem to get my same printer working. did you ever figure it out?

---

### Post by dorhelp on 2006-10-19
I set my windows printers up as lpr printers than you don't use samba to print. In XP you look under network connections Advance menu add Other Network Options than unix print support. After that you can add them to cups as lpr printers I am not at the location where they are installed but I am sure the address is lpd://server/quenue
                    Good Luck
                    Linda

---

### Post by shanepardue on 2006-10-19
i got it working. what fixed it was...setting the paper size to letter through [http://localhost:631/](http://localhost:631/) and not just through cups manager. now i'm printing with great margins on all of my computers in the network!
Edit/Delete Message

---

