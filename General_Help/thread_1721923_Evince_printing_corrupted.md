---
title: "Evince printing corrupted"
date: 2011-04-05
forum: General Help
---

### Post by garethfoxwilliams on 2011-04-05
A Pdf created in either OOo or Gnumeric and viewed in Evince will display perfectly on the PC. 

However, when printed, various letters or numbers will be sustituted with blanks, boxes or other characters.

The printer is an HP 2280 Business Inkjet on a JetDirect printserver, and I've not had any problems with it before on previous Ubuntu versions.

The suspect Evince version is 2.32.0 and this phenomenon happens on three different machines running 10.10. ( 2 Ubuntu, one Xubuntu) 

Another machine running 10.04 ( Evince 2.30.3 ) prints perfectly.

To test further, I installed Xpdf on one 10.10 machine and that prints perfectly.

Has anyone encountered similar problems or could anyone suggest a solution?

---

### Post by garethfoxwilliams on 2011-04-08
Any ideas, anyone?

---

### Post by rvchari on 2011-04-08
> **garethfoxwilliams said:**
> A Pdf created in either OOo or Gnumeric and viewed in Evince will display perfectly on the PC. 

However, when printed, various letters or numbers will be sustituted with blanks, boxes or other characters.

The printer is an HP 2280 Business Inkjet on a JetDirect printserver, and I've not had any problems with it before on previous Ubuntu versions.

The suspect Evince version is 2.32.0 and this phenomenon happens on three different machines running 10.10. ( 2 Ubuntu, one Xubuntu) 

Another machine running 10.04 ( Evince 2.30.3 ) prints perfectly.

To test further, I installed Xpdf on one 10.10 machine and that prints perfectly.

Has anyone encountered similar problems or could anyone suggest a solution?
my evince version is 2.32.0 and its functioning perfect. earlier i used OOo, now migrated to libre office. i can view, print and get the same patterns and visuals without any missing.

i also tried to pdfs created in virtual xp thru ms office and viewed it with evince and printing it. its perfect... funny y u r facing problems with 3 machines !

try to remove evince and re install

"sudo apt-get purge evince" and "sudo apt-get install evince"

can also use software center. try this. if there is any currupted file in evice install then it will be removed. try this in one machine and check out... if your problem is solved, repeat it in the other 2 machines...

---

### Post by garethfoxwilliams on 2011-04-14
I've re-installed evince and CUPS as described above, but sadly no difference.

I'm intrigued that Xpdf prints OK whereas evince does not. Does it use a different set of drivers?
I have re-installed the printer Hplip

---

