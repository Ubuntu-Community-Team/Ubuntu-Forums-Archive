---
title: "document viewer failing to print pdf documents"
date: 2010-01-20
forum: General Help
---

### Post by irishwoody on 2010-01-20
Hi there

Been using ubuntu for several months now (trying not to boot windows)

Have an issue with printing.
1. Using the document viewer I press print to print a pdf file (network printer) and it enters the print queue - I see it processing; then job complete - but no paper comes out of printer.

2. same file - using GIMP or ePDF - jobs completes and prints successfully.

Setup
Ubuntu 9.10; 2.6.31.17-generic-pae
printer : Generic-35C-4-series
dnssd://Generic%2025C-4(5D%3AF5%3A22)._pdl-datastream._tcp.local/

woody

---

### Post by hsmak_linux on 2010-01-20
Hey there,

Well, I'm facing same problem. Although I'm using an HP printer but this might help you.

After doing a little search on this issue, it appears to me that there is no direct way to print PDF files.

So, check this thread first and see under which your problem might fall (*apparently, mine is the 3rd*):
[CUPS Server Won't Print PDF]("http://ubuntuforums.org/showpost.php?p=5633128&postcount=4")

This gives you a hint that to print a PDF file you need to convert it to PS file (*I tried this but what was printed was garbage lie binary numbers*).
[Bypassing PDF to PS Conversion (Printing PDF Files Directly)]("http://hplipopensource.com/node/300")

So, this is what I did:

[LIST=1]
[*]Open the PDF file
[*]ctrl + p
[*]Print to a file --> make sure that PS extension is chosen
[*]Open the created file
[*]Print it
[/LIST]

Good luck!

---

### Post by slamhound on 2010-01-20
Yeah, I have this same problem.  Never happened on 9.04 (with same computer/networked printer). It even worked for a little bit after switching to 9.10.  But for the last month it doesn't work.  

Xpdf can print the same document with no problems, only gets screwed up with Evince/Document Viewer.

---

### Post by hsmak_linux on 2010-01-20
> **slamhound said:**
> Yeah, I have this same problem.  Never happened on 9.04 (with same computer/networked printer). It even worked for a little bit after switching to 9.10.  But for the last month it doesn't work.  

Xpdf can print the same document with no problems, only gets screwed up with Evince/Document Viewer.

I've just tried the XPDF. the great thing is that it really worked and it was printed!
At least we have an alternative.

Thx dude!

---

### Post by pertti on 2010-01-21
I'm having the same problem with printing PDF files with Evince. I can't use xpdf, since I need to print my documents on both sides manually and xpdf doesn't allow me to print just even or odd pages.

I tried printing the PDF to PS with Evince and then printing the PS file. It seemed to work, but then I noticed that whether I select even or odd pages it always prints odd pages! :( I will be reporting this on Launchpad.

---

### Post by pertti on 2010-01-21
Hmmm, it seems that it is somewhat related to HP printers. Printing  to a HP LaserJet 2300 doesn't work, but printing to a Dell 3100cn does. However, it's quite strange, because it's the combination of Evince + PDF + HP that seems to fail...

---

### Post by slamhound on 2010-01-21
My problems are with a Dell MFP1815dn.  So unless this is somehow really an HP printer with Dell branding, it seems to extend beyond HP printers.

And yes, I agree that Xpdf isn't an ideal solution for reasons like those you mentioned.  I find myself using Evince for some things but then switching to Xpdf when I need to print.  Not the most convenient solution.

---

### Post by foleyfresh on 2010-01-24
I'm having the same problem with HP Laserjet 4200n. Thanks for the Xpdf tip

---

### Post by slamhound on 2010-01-25
This might be fixed.  Looking over the bugs on Launchpad, it looked like it might have had something to do with Cairo.  Today there was an update in libCairo that had something to do with pdf printing problems.  Tried printing a pdf before the update--didn't work.  Installed the update, rebooted, tried the same pdf again, and it worked! Haven't done extensive testing with different pdfs, but hopefully this is a fix.

---

### Post by gruntlips_ on 2010-01-26
Slamhound, is this the bug you refer to? And if so, where did you download the libcairo update and how did you install it?

Thanks.

[https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/227186](https://bugs.launchpad.net/ubuntu/+source/cairo/+bug/227186)

---

### Post by slamhound on 2010-01-26
I think it was this one (though I did poke around in a couple different ones that had related symptoms):

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/419143](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/419143)

The update came through the automatic updates in Update Manager.

---

### Post by buster65 on 2010-01-31
I'm having the same problem with 3 Epson printers 2 are networked and the other is USB. I can print with all the other apps but not Document viewer.

---

### Post by johngrey on 2011-02-22
Did anyone get anywhere with this?

I've just started having this problem when trying to print to an HP1020 from Document Viewer (it was OK last week before I installed a number of regular updates including an update to the Adobe Reader 9).  

Printing documents go into the print queue, but then give an error 'There was an error processing job *filename*...'

I can successfully print the same pdf files from Adobe Reader 9.

Using Ubuntu 10.04 LTS

[edit to add] - I can also print the same files OK from Okular

---

