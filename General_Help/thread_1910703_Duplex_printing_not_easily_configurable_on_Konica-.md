---
title: "Duplex printing not easily configurable on Konica-Minolta Bizhub C552DS"
date: 2012-01-17
forum: General Help
---

### Post by bartonski on 2012-01-17
I'm running Lucid. I set up printing to a Konica-Minolta 'Bizhub C552DS'.

One-sided printing seems to work correctly. The 'Duplex' option in printer properties is, however, ghosted.

The unit is a combination printer/fax/copier/scanner, the copier has the ability to print duplex -- so I know that the machine has a duplex tray.

I have tried two different ppd files: 

First I used

/usr/share/ppd/openprinting/KONICA_MINOLTA/KOC550UX.ppd.gz

After some googling, I downloaded and tried KOC652UX.ppd [downloaded from [http://onyxftp.mykonicaminolta.com/download/SearchResults.aspx?productid=1183](http://onyxftp.mykonicaminolta.com/download/SearchResults.aspx?productid=1183)]

The second driver allowed me to choose my exact printer model from a list... but the duplex drop down is still ghosted under properties.

If I click on 'Device' tab, there is a 'Print Type' option which can be set to '1-sided' or '2-sided'... this works, but it's one of about 50 different options... not something that you'd want to have to hunt down every time you wanted to change from simplex to duplex or vise versa.

If anyone knows of a better ppd to use for this printer, I'd like to know.

---

### Post by chronos00 on 2012-08-03
I am also having this problem.

But If I select the '2-sided' on the 'Device' tab, the option is still ghosted at the print dialog, when I try to print from any program.

I have a Bizhub 283, and I am using [this driver (KO423SX.ppd)]("http://onyxftp.mykonicaminolta.com/DownloadFile/Download.ashx?fileid=21437&productid=1316") downloaded from [this page]("http://onyxftp.mykonicaminolta.com/download/SearchResults.aspx?productname=283").

Am I doing anything different?

---

