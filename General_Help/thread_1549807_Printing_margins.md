---
title: "Printing margins"
date: 2010-08-10
forum: General Help
---

### Post by sapoleon on 2010-08-10
Hi all, 
I have an HP Deskjet D1460. 
I am using Ubuntu 10.04 and HPLIP 3.10.2 that came with the distro. 

I am in a plan of moving my windows PC to ubuntu in my bussiness, and this is the first of them. Trying to solve all the problems before converting a second one. 

All seems to work quite well and almost out of the box... and that is a huge step from the last distro i tryied 2 years ago. 

So, my difficulty now resides on the printing. I am using a small VFox program that manage some of the aspects of the bussiness, in wine. It works without problems, but... when I print, all the pages get printed like 1cm below than when it was printed under windows. The problem is, that I use the printer to fill some forms that came pre-printed, and now, I am printing over the other text instead of the white spaces.

I read a little, and try to adjust the HWMargins and the ImageableArea in the ppd of /etc/cups/ppd/ but it was like if I was doing nothing...

Do I miss a step? Do I need to restart a service or something after changing the ppd?
The margings when using the printer gui from Ubuntu are all in 0, and for that i need like a minus something... 

I will appreciate any help.

Thanks

---

### Post by baddnady23 on 2010-08-10
I have a similar problem and have been unable to resolve it as of yet with an HP.  I have seen others recommend to go into CUPS and make sure that the default page size is set to "Letter" (as long as thats the paper you are actually working with) and to also go into the system>printing preferences and make sure it is also set at letter.  Like I said, others have reported success but I still haven't been able to fly that flag.

---

### Post by sapoleon on 2010-08-13
Hi baddnady23, 

I am using A4, and CUPS is in A4 so.. nothing to do.

It prints great, but... low :(.

Don't anybody have a clue about this?

Thanks for your reply

---

### Post by manthony121 on 2010-09-02
I don't have an answer, but more info.

I use an HP Laserjet 6P at my office.  When printing directly from the command line, all is good: 'ls|lp' gives a nice print out.  However, whenever I would try to print a web page, or print a pdf file from evince, acroread, or xpdf, the very top of the page would not print.  I was able to fix that by adjusting the "Imageable Area" setting in the pdd file, moving the UR corner up a bit.  After I did that, however, the 'ls|lp' command produced output closer to the top of the page, with the tops of the characters cut off.  I set a default using 'lpoptions' to enlarge the top margin a bit, and now both work OK.  The pdf printing does not seem to recognize the "-o page-top=35" option, but the direct printing does.

So, some programs seem to bypass CUPS options such as "-o page-top=35" and put the print image on the page at an absolute location, while other programs DO respect CUPS margins.

---

