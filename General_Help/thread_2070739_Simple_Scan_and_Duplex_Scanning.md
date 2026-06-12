---
title: "Simple Scan and Duplex Scanning"
date: 2012-10-13
forum: General Help
---

### Post by david.rahrer on 2012-10-13
I'm confused about how Simple Scan is supposed to work in this instance and I've found next to no documentation to explain it.  One snippet did seem to indicate that, using an ADF (automatic document feeder), and setting SS preferences to scan "Front & Back" then choosing "Scan All Pages from Feeder" that is should scan all the pages in the tray, then pause and prompt to put the stack back in upside down.  After that, it should scan those and then stitch them all together in the correct order.

I'm running Ubuntu Precise 64 (but it does the same thing on Lucid 32) and scanning with an HP Officejet 5610.  When I try the above, the first run stops just short of ejecting the last page after scanning the stack, but does not ask for any more.  If I pull the last page out and place the stack back in reversed anyway, and start the scan again, it just adds the pages but does not stitch them.  I've also tried setting preferences to scan "Front" and then "Back" manually but I get the same result.  

I am currently using Simple Scan 3.4.1 from the official repositories.  I've tried starting it from the command line to see if it throws any errors during the entire process, but it does not.  This particular All-In-One has always been compatible and I don't have any other issues.  The scans I do make are great.  I could install other software for this but if SS is supposed to do the job, I would much rather keep it simple. 

I would really appreciate any input on how this is supposed to work before I submit a bug report.  I may just be missing it, but I've not found any reports on this so I honestly don't know if it should work differently.

Thanks.

---

### Post by zero2xiii on 2012-10-13
Hay,

Strange questions:
Have you tried with first only a few pages? Say 4 or 5 just to see if the actual process fails?
And have you tried an older version to see if it might be a new bug?
How about the printer drivers, are they up to date?

Cherz

---

### Post by david.rahrer on 2012-10-13
Thanks, here are my responses:

1. Yes, I tried with just 3 pages and it does the same thing.

2. Yes, I've tried with both the version in Lucid and the one in Precise, both with the same results.

3. The HP drivers are the current available for each respective version of Ubuntu.  I promptly install all available updates in the main channel and I monitor the backports and proposed.  

Is the process I described how SS is supposed to work, i.e. should it be asking for the reverse sides and stitch them together after as I described?

---

### Post by andresimi on 2012-12-18
I am having the same problem/doubt... And I am using the HP Officejet J4660. One alternative is to use gscan2pdf, but gscan2pdf makes huge files.
Simple Scanner is so much better, it would be so nice if it worked!

---

