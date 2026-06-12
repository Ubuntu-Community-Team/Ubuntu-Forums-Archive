---
title: "Can no longer print - Canon MX-860 on Karmic Install"
date: 2009-11-07
forum: General Help
---

### Post by csete on 2009-11-07
Hello,

I'm having trouble with my laptop printing to a Canon MX-860 since my update to Karmic.  Before the upgrade I had downloaded and installed the drivers as described in this thread: [http://forums.linux-foundation.org/read.php?25,9006,9786](http://forums.linux-foundation.org/read.php?25,9006,9786) .  This was working well.  Since the upgrade, printing jobs sit at "Processing" forever and are never actually printed.  I've uninstalled and reinstalled the printer in printer configuration and it finds the printer on the network (it is connected directly to the network via Ethernet cable) and seems to find the driver as well.  I've also tried reinstalling the drivers as directed in that thread.  (NOTE: AMD64 installation using --force-architecture).

The laptop in question is an Inspiron E1505 running Karmic 64 Bit.  Any insights on how to troubleshoot this would be greatly appreciate.  

Thanks,
Craig

---

### Post by csete on 2009-11-07
I've made a small amount of progress on this issue.  I've found that I can print a test page to the printer, but not the PDF document that I was originally trying to print.  I see when printing the test page that I get the following logged:

```

D [07/Nov/2009:21:54:31 -0600] [Job 18] pstocanonij: /usr/bin/gs -r600 -g5100x6600 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/bin/cifmx860 --imageres 600 --papersize letter --media plain --paperload auto --bbox 18,14,595,784 --fit  

```

as well as:

```

D [07/Nov/2009:21:56:00 -0600] PID 5240 (/usr/lib/cups/backend/cnijnet) exited with no errors.

```

The PDF file doesn't seem to ever be handled by the Canon driver:

```

D [07/Nov/2009:21:58:22 -0600] [Job 19] Running /usr/bin/pdftops  -level2 -origpagesizes /tmp/pdftops.zRTbqx -
D [07/Nov/2009:21:58:22 -0600] [Job 19] Running pstops '19' 'xxxx' 'PDF Statement' '1' ' MediaType=plain InputSlot=auto Duplex=None PageSize=Letter CNExtension=2 job-uuid=urn:uuid:3b5fa8b7-e17a-3abe-4798-b4ad683b33d1 job-originating-host-name=localhost'

```

with no call to the backend.  It appears that something isn't set up quite right in my filters, but I don't know how to go about fixing this up.  Any suggestions would be appreciated.

Thanks,
Craig

---

### Post by DedMoroz on 2009-11-09
Ive noticed this also. All PDFs no longer print in Ubuntu 9.10

---

### Post by kevindontenville on 2009-11-12
I managed to print one PDF page, then it appears to print, heads of to print queue on CUPS and quietly dies and shows as printed.

Seems odd, must be a fair few people do this but I don't see PDF problems all over the place. I will update my server CUPS and see if it lies there and dig a little further.

Edit:  Just updated CUPS and tried printing from Karmic but still the same result. Printing same pdf file from Windows works fine to the trusty Hardy server.

---

### Post by csete on 2009-11-12
I will be interested in anything you uncover.  One note... I don't have a server CUPS involved... this is all with the CUPS local to my laptop talking direct via Ethernet to the printer.  Works fine for test page, but not PDF.  It seems like it has something to do with the filter chain or backend, but I'm not sure what or how to figure it out.

---

### Post by rmcd on 2009-11-14
Same problem here. I can print a test page but pdfs over a network under karmic simply fail to print. Everything worked fine under Jaunty. I have had mixed success using acroread instead of evince, but that doesn't always work.

(In the original post I forgot to say that both are HP printers: a 1320 that is directly networked, and a 2300 that is hooked up to a CUPS server.)

---

### Post by UeB on 2009-11-15
I have a similar Problem with a HP Laserjet 4050

It worked fine in 9.04 but since I upgraded to 9.10 I cannot print pdf files with evince, although printing the "print test page" works fine!

There is no obvious error mesg. And in the printer queue history all my attempts to print a pdf file with evince are marked as successes! But nothing came out of the printer.

anybody any suggestion what to do?

---

### Post by UeB on 2009-11-21
anybody anything now on the subject?

I still cannot print anything despite the test page. Have to print everything at work at the moment. Not the optimal solution...

---

### Post by UeB on 2009-11-21
After some google search I found that in my case the Problem is related to this bug:
[https://bugs.launchpad.net/ubuntu/karmic/+source/evince/+bug/419143](https://bugs.launchpad.net/ubuntu/karmic/+source/evince/+bug/419143)

Workaround is to use a non gtk app for printing pdfs like okular instead of evince.

---

### Post by csete on 2009-11-29
I can validate the using Okular works for me as well to print PDF files.  Looking forward to a fix for the GTK handling.

---

### Post by rmcd on 2009-12-11
I have had the same problem printing pdfs in 9.10 and am now using Okular, but Okular has introduced new problems.

1. On first print of a document Okular *always* tries to print A4. This causes a printer error. The system default is letter and Okular says it's default is letter, but I have to go into print options every time and explicitly select letter in order for the document to print. 

2. Many printer options, for example, duplexing, are grayed out in the okular print dialog and cannot be changed. The grayed out dialog says duplexing is off, but everything prints duplex. If I am going to print pdf, it *has* to be duplex (since only okular will print it). This is a problem for some documents.

I am printing over the network via cups. Local printing from the server works fine. And printing over the network worked perfectly in 9.04.

Suggestions?

---

