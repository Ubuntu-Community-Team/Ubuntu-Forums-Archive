---
title: "HP D1660 Printer install in Lucid"
date: 2010-06-18
forum: General Help
---

### Post by dartmusic on 2010-06-18
I just bought the above-mentioned printer (Microsoft store for $15!) and when I ran into problems last night installing it I was unable to come up with a concise answer to the issue I was having and thought that I would share my experience.

This is a fairly basic/standard Lucid install and I've never had any other printer connected.

I opened the box and put everything together as noted in the quickstart poster with the exception of using anything on the included CD.  When I plugged the USB cable in, the printer was recognized right off the bat and I got a popup noting such and stating that it was ready to print.  I went to System/Admin/Printing and tried printing a test page.  The test page showed up in the queue and said it was completed, yet the printer did nothing.  I tried printing from OpenOffice and still nothing.

I then installed everything I could find that seemed reasonable in Synaptic after searching for hplip, including the (wonderful) GUI app.  That is literally all it took and I was able to print.  At this point there are two printers installed so I had to delete the one that was already set as the default (and not working correctly) and set the newly installed printer as the default and everything works as it should.

Hopefully this will be helpful to someone.

---

### Post by xisxas on 2010-08-07
dartmusic

You made the installation very easy. Thanks.



Hello Steve

---

### Post by volaer on 2010-08-07
I am trying this one right now. I have the same printer but not working.

---

### Post by Butthead on 2010-08-07
Try running HP-setup in terminal.

If that doesn't work, go to the HP drivers page and follow their D1660 install procedure.

---

### Post by PeterDrop on 2010-08-07
> **Butthead said:**
> Try running HP-setup in terminal.

If that doesn't work, go to the HP drivers page and follow their D1660 install procedure.
i follow the indications, on hp drivers, i have the hp device manager, but i can print a test page, and say " startting job" and "job completed" but nothing happens :(

---

### Post by volaer on 2010-08-07
> **PeterDrop said:**
> i follow the indications, on hp drivers, i have the hp device manager, but i can print a test page, and say " startting job" and "job completed" but nothing happens i follow the indications, on hp drivers, i have the hp device manager, but i can print a test page, and say " startting job" and "job completed" but nothing happens :(


Same thing happening here....

---

### Post by volaer on 2010-08-07
OK.... already solved this. Follow instructions:

Go System> Administration> Printing

Right Clcik Deskjet d1600 series

Click properties

Click Settings

"Change" in Make and Model bar 
....it will search for driver

Click HP, click deskjet 1600 series

Choose the driver HP Deskjet D1600 Series, hpcups 3.10.2

Mine is working now... Please let me know if your HP D1660 is now working as well.

---

### Post by KinGnu on 2010-08-08
Dude That was excelente!!!! it worked for me!!!! You are awesome!

---

### Post by volaer on 2010-08-08
> **KinGnu said:**
> Dude That was excelente!!!! it worked for me!!!! You are awesome!

I found out that this printer only work with CUPS....

---

### Post by triscones on 2010-10-19
Have tried all of above with no luck.  

I remember there being a specific driver for the d1660 but cant find it any where.  Also having problems with setting up my terminal and the logon settings.

Help is much appreciated so I can get my online printing contracts and invoices for my business again and thus making money, not losing $$ :mad:) 

:?

Many Thanks, 
Tg

---

### Post by volaer on 2010-10-20
> **triscones said:**
> Have tried all of above with no luck.  

I remember there being a specific driver for the d1660 but cant find it any where.  Also having problems with setting up my terminal and the logon settings.

Help is much appreciated so I can get my online printing contracts and invoices for my business again and thus making money, not losing $$ :mad:) 

:?

Many Thanks, 
Tg


I really wonder why you can't get it dude. This printer only works with CUPS... you have to activate your CUPS. That's the driver you need. 

Simply follow my instructions above. If you have no CUPS, try to install it from the repositories. 

NOTE: THere's a bug though. Mine doesn't print multiple pages. For example, I will be printing 5 pages, I need to print them one by one.

---

### Post by TheTinyt1 on 2010-10-31
I have just purchased his same printer for a cheap printer that I thought would print easily with 10.04 64bit. I have never found an  HP that would not. however, I have not found one that is recognized but will not print.  

I have done everything you suggested and then some. No printing at all. It says it is printing and that the print job is complete but no go with anything being physically printed.

What gives???

Thanks for any help here...


Bright Blessings
TheTiny1

---

### Post by 1005703 on 2010-11-10
Hi volaer,

I have followed your destructions below, choosing the only driver made available to me: HP Deskjet d1600 Series hpijs, 3.10.2.  Is this different to the driver you mention?  I checked in my Software Centre and I do have CUPS installed.  Help?

> **volaer said:**
> OK.... already solved this. Follow instructions:

Go System> Administration> Printing

Right Clcik Deskjet d1600 series

Click properties

Click Settings

"Change" in Make and Model bar 
....it will search for driver

Click HP, click deskjet 1600 series

Choose the driver HP Deskjet D1600 Series, hpcups 3.10.2

Mine is working now... Please let me know if your HP D1660 is now working as well.

---

### Post by shrimpy89 on 2010-12-07
I had the same problem.  But under hpijs was the hpcups driver for me.  Dunno why it would be missing.


I also wanted to say thank you to Volaer.  The solution worked for me.

---

### Post by nkoontz93 on 2011-03-14
I'm running 10.10, and it worked great. Just a different driver name but it was easy enough to figure out. Thanks:D:D:D

---

