---
title: "Document View Refuses to Print PDF"
date: 2010-11-28
forum: General Help
---

### Post by Joseph Schwenker on 2010-11-28
I just tried to print [this PDF]("https://docs.google.com/viewer?url=http://www.vendian.org/mncharity/dir3/paper_rulers/UnstableURL/rulers_metric.pdf"), and the document viewer (evince) refused to print it, delaying a minute until the printer started, then printing insanely slowly, in short little bursts.  All other applications seem to work fine.
I was, in the end, able to print the document through GIMP.  I'm on Ubuntu 10.04 32-bit.  Can anyone reproduce this?  I have the HP PhotoSmart C4100.

---

### Post by dcstar on 2010-11-28
> **Joseph Schwenker said:**
> I just tried to print [this PDF]("https://docs.google.com/viewer?url=http://www.vendian.org/mncharity/dir3/paper_rulers/UnstableURL/rulers_metric.pdf"), and the document viewer (evince) refused to print it, delaying a minute until the printer started, then printing insanely slowly, in short little bursts.  All other applications seem to work fine.
I was, in the end, able to print the document through GIMP.  I'm on Ubuntu 10.04 32-bit.  Can anyone reproduce this?  I have the HP PhotoSmart C4100.

Won't print on my 10.04 system with a Brother printer - the pdftops process gets stuck in a loop and never seems to complete sending the job to the printer.

Report it as a bug.

---

### Post by Joseph Schwenker on 2010-11-28
How do I report bugs?  Where should I report it?

---

### Post by cabinetman on 2010-12-02
This is a workaround. Install xpdf from the software center. If you are downloading the pdf file save it. Then right  click on it and open with xpdf. Then you can print  it to a file that I save on desktop, close xpdf and click on *.ps file that you saved and then go file print. The command to print that comes up on xpdf is lpr, maybe someone else knows the command to send it to your printer. This worked for me on files downloaded from the internet. Pdf files exported from open office print fine.

I later installed adobe reader 9 and it printed without any problems

---

