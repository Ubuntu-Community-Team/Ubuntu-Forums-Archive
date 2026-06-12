---
title: "Printing pdfs with evince in 10.04"
date: 2010-07-28
forum: General Help
---

### Post by rmcd on 2010-07-28
I find that some pdf files will not print properly in 32-bit 10.04 using evince. The document is sent to the printer and then the printer simply flashes and never prints the document (I have waited an hour). The same documents *will* print quickly when I print with acrobat reader, although when using reader the the following error message appears in the terminal:

(acroread-en:3915): Gtk-CRITICAL **: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed

The printer is a lexmark X364-dn. The problem seems particularly acute with documents that have been scanned. 

Any suggestions?

Thanks, 

Bob

---

### Post by jobix on 2010-07-28
Did you install the correct drivers for your printer?
Also, I'd try deleting the printer from your setup and re-install it again and see if that makes a difference.

---

### Post by philinux on 2010-07-28
rmcd,

to rule out the printer or the system. Enable the partner repo and instal acroread. If it prints fine then file a bug against evince.

---

### Post by Janeleaper on 2010-07-30
I have also got this problem.  The printer is a HP deskjet 845C.  It prints a test page and will print open office documents, but nothing happens when I try to print a pdf from Evince.

Amending this post:  Only some pdfs refuse to print.  Unfortunately they are the ones I need!

---

### Post by hyperboloid on 2010-08-17
I also have this problem, running 10.04 with an HP LaserJet-3015. Some PDFs print just fine, some take 5 minutes or more per page, and some just never print at all. This happens mostly in evince, but even acroread can be quite slow for some PDF files. 

Printing on this printer was absolutely flawless until Ubuntu 9.10, and has kinda sucked for the past year. This is a big issue and I don't know why it hasn't gotten more attention in the forums. 

How many other people out there are having trouble printing PDF files with 9.10 or 10.04? Please speak up!

---

### Post by cerda on 2010-09-09
I'm too having these problems while trying to print a PDF file from evince. It's really annoying, i noticed when i try to print, the job goes to the printer but its too big like 20mb for a 20 page document, and it never reaches the printer, or sometimes it prints the first page and stops.

Also using ubuntu 10.04

---

### Post by kuntzmann on 2010-09-10
We are also having problems printing pdf's using evince in lucid
When we print to Ricoh mp c3300 or c5000 it completely locks up the printers, necessitating a reboot. On hp printers and canon copiers the printers will say processing, but nothing ever comes out. If someone wants to test a pdf that does this, you can use the California drivers license manual, just google DL600, download the pdf and try to print it. Printing from Adobe 9 does work. Have also used other pdf viewers and they also print without issue.

---

### Post by francesco1964 on 2010-09-24
I've the same problem with evince/lucid on toshiba e-studio 232, some pdf won't print, requiring printer reboot. The same pdf will print from Acrobat on a WXP PC.

---

### Post by varanasi on 2010-09-29
Yep.  Me too.  Sometimes evince locks up.  Sometimes evince then locks up the whole computer.  (It's a problem that I had long ago, but haven't experienced recently.)

---

### Post by Doc on 2010-10-01
I've had the same issue with my Dell S2500 printer (which is a re-branded Lexmark) for the first time since upgrading to 10.04, though I've had this printer for years and never had a problem up until now. Postscript files won't print either. I doubt it's an evince problem, because trying to print from the command line also doesn't work...the funny thing is there isn't even an error message, cups thinks the job was successful. Caveat: I am using a netgear network print server...I'll try connecting that directly to the computer later and report back if that makes a difference (though I doubt it, it worked fine in prior Ubuntu versions). 

The workaround for me is to convert the pdf to a ppm file, using pdftoppm. These seem to print reliably. You may need to apt-get install netpbm to get the conversion tools. (I did construct a crude nautilus script to do this graphically instead of using the command line, and can post it if anybody is interested. Saves some time and a bit of annoyance.)

hs

---

### Post by ShyTot on 2010-10-14
Yes, me too printing PDFs from evince.

It starts printing quickly, then slows down to an absolute crawl, maybe taking 3 minutes to print each page.

---

### Post by ShyTot on 2010-10-14
> **ShyTot said:**
> Yes, me too printing PDFs from evince.

It starts printing quickly, then slows down to an absolute crawl, maybe taking 3 minutes to print each page.

Adobe Reader 9 prints the PDFs fine.

---

### Post by craig100 on 2010-11-07
I also have this problem running 10.10 Meerkat x64 with an Epson Stylus Photo PX710W printer.  Everything prints ok except when I print a PDF from Evince that has colour images embedded.  It prints black and white with no problems.  With colour it starts slow and slows down so it never finishes (even after 30 mins).

---

### Post by gobbles414 on 2010-11-21
Adobe Reader will not print PDFs to my wireless Brother MFC-490CW in Ubuntu 10.10 (32-bit, proposed updates enabled), but Document Viewer prints them flawlessly. I suspect a bug in the acroread package.

---

### Post by tim.hoeffel on 2011-07-26
> **gobbles414 said:**
> Adobe Reader will not print PDFs to my wireless Brother MFC-490CW in Ubuntu 10.10 (32-bit, proposed updates enabled), but Document Viewer prints them flawlessly. I suspect a bug in the acroread package.

I'm having a similar problem with NN 11.04 and Acrobat. Some file will print, some will not. I need a solution to this because I need to print stuff for work.

---

### Post by pangea on 2011-07-29
> **tim.hoeffel said:**
> I'm having a similar problem with NN 11.04 and Acrobat. Some file will print, some will not. I need a solution to this because I need to print stuff for work.

I too have been having this problem both through envince and Adobe Reader. The reliability of printing pdfs is highly erratic. Sometimes they work, sometimes they do not. The most success I have is choosing to print single pages at a time. I have had no success If I try to to multiple pages to a sheet or change the page orientation.Sometimes the printer spins up but nothing comes out and sometimes absolutely nothing happens. On all occasions though CUPS indicates that the job was successful.

I am using a Dell 2330dn printer connected on LAN with a fixed IP. I am currently using the ppd files/drivers supplied by Dell for previous versions of Ubuntu. 

I've tried several different set ups including generic set up with generic drivers. 

Would love to have some assistance or guidance as to how to fix this as it's the only thing holding me back from going full time to Ubuntu.

---

### Post by Doc on 2011-07-30
There may be more than one bug causing the problems in these posts, but on my system I believe this may have been caused by some stale configuration files left around after an upgrade. If you have a fresh install this is probably not your problem. In order to fix it I (first backed up and then) deleted the following files in my home directory:

.config/
.gconf/
.gconfd/
.gnome2/
.local/

Warning: in deleting these files you will lose some personalized settings in your applications you may have stored. You will also need to log out and log back in. I haven't had any problems since I did this.  

hs

---

### Post by pangea on 2011-07-30
> **pangea said:**
> I too have been having this problem both through envince and Adobe Reader. The reliability of printing pdfs is highly erratic. Sometimes they work, sometimes they do not. The most success I have is choosing to print single pages at a time. I have had no success If I try to to multiple pages to a sheet or change the page orientation.Sometimes the printer spins up but nothing comes out and sometimes absolutely nothing happens. On all occasions though CUPS indicates that the job was successful.

I am using a Dell 2330dn printer connected on LAN with a fixed IP. I am currently using the ppd files/drivers supplied by Dell for previous versions of Ubuntu. 

I've tried several different set ups including generic set up with generic drivers. 

Would love to have some assistance or guidance as to how to fix this as it's the only thing holding me back from going full time to Ubuntu.
Just an update to mine. I reinstalled the printer using the Generic PCL 5e Printer Foomatic/hpijs-pcl5e. This has sped up the printing of pdf but I still cant alter the file to print multiple pages per sheet or change the orientation.

I am using Natty 11.04.

---

### Post by dcstar on 2011-07-31
I have the same issue in my 10.04 system with PDF's from particular websites.

I installed the **xpdf** package and that prints the PDF files that the standard Evince Document Viewer can't.

---

