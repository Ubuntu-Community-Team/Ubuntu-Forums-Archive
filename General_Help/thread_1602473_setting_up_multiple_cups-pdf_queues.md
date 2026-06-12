---
title: "setting up multiple cups-pdf queues"
date: 2010-10-21
forum: General Help
---

### Post by wililupy on 2010-10-21
Hello,

I have an Ubuntu Server running CUPS-PDF successfully. The problem that I am running into now is that we want to have different CUPS-PDF queues.

Example:

Joe from Finance wants his PDF prints to go to /home/finance which is samba shared out to all users in Finance. 

Mark from Operations needs logs printed out to /home/ops which is samba shared to all users in Operations and must be landscape.

Finance and Operations print from the command line (lp -d print-queue filename) on the server via ssh since their app runs from a terminal.

I have looked and looked all over the net and through the cups-pdf documentation to see if there is a way to force the URI for the cups-pdf print queue instead of it going to the default of $HOME/Desktop as stated in my /etc/cups/cups-pdf.conf file. 

Basically, I want to set up a cups pdf printer called Finance, Advert and Ops that has all the options they need so when they print something from the linux applications, and they tell it to print to the virtual printer that they have permission to use and it go to the respective directory that they have access too.

Any help would be greatly appreciated.

---

### Post by sbarrow on 2011-01-03
Did you get this working? I'm trying to do the same thing and not sure where to start.

---

### Post by tahoekid on 2011-08-08
I have looked into this as well, and it appears not possible given the current cups-pdf software. There's no command line option for this. 

In addition to re-directing output, it would be useful to have the printer driver generate PDF files in parallel, instead of a queue. Since this is not a real printer, it seems it should be possible to have simultaneous files generated. (Again, I've not found this to be possible either).

---

### Post by hausrath on 2011-11-20
I had the same issue a couple weeks ago and was finally able to devise a solution.  Although it's not currently supported via the default cups-pdf installation, it's quite easy (IME) to manually build cups-pdf and specify the configuration file the queue will use.

Just download and extract the current source tar.gz from [http://www.cups-pdf.de/download.shtml](http://www.cups-pdf.de/download.shtml).  Put it somewhere you can work on it (you'll copy the resulting file to where it needs to go after you compile).

Then modify the following line specifying the configuration file in cups-pdf.h to suit your needs:
```
#define CPCONFIG "/etc/cups/cups-pdf.conf"
```Then modify cups-pdf.c to make each instance of "cups-pdf" distinct (I did it by changing them all to "cups-pdf-instance2").  So for the second instance of cups-pdf I wanted to run, I modified the following line (currently #584):
```
    printf("file cups-pdf-instance2:/ \"Virtual PDF Printer\" \"CUPS-PDF-instance2\" \"MFG:Generic;MDL:CUPS-PDF-instance2 Printer;DES:Generic CUPS-PDF-instance2 Printer;CLS:PRINTER;CMD:POSTSCRIPT;\"\n"); 
```I think all that really matters is changing the path where the "printer" is referenced, which is "cups-pdf:/", but I changed everything just for consistency's sake.

Then compile and copy the resulting binary to CUPS backend directory.  To do that, all I did was run:
```
sudo gcc -O9 -s -o /usr/lib/cups/backend/cups-pdf-instance2 cups-pdf.c
```from the directory where my cups-pdf.h and cups-pdf.c were located.  (The details are all specified in [http://www.cups-pdf.de/documentation.shtml](http://www.cups-pdf.de/documentation.shtml).)

Then make the permissions right on the resulting binary and restart cups:
```
sudo chmod 700 /usr/lib/cups/backend/cups-pdf-instance2
sudo service cups restart
```Be sure you have a cups-pdf.conf in the location you specified earlier in cups-pdf.h.

Like I said, I did this a couple weeks ago so I'm a little fuzzy on the details - but I think this was all I had to do to get it to work.

My reason for doing it was to configure multiple output directories, but also to then email the resulting file to a preconfigured email address.  So a different email address would receive the PDF as an attachment, depending on the printer that was selected.

---

