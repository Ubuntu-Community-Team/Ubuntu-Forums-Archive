---
title: "Thick black lines sometimes appear on printing"
date: 2010-02-22
forum: General Help
---

### Post by Azdour on 2010-02-22
Operating System: Ubuntu 9.04
Printer: LaserJet CM1312 MFP

I have an intermittent printing issue that results in part of a printed page containing a horizontal line that spans over two lines. The line is mostly black, with the occasional small break where there seem to be printed multiple characters printed over each other.

Sometimes I print and I do not get this issue. Other times I can print 60+ pages and it happens, while sometimes I get it on a single page being printed.

I'm not sure if this is a driver, printer or cable issue. We've used it through CUPS and we've used a print hub to convert the USB to a network accessible printer to see if that made any difference but it did not.

I have a feeling this has something to do with the print job data corruption.

---

### Post by Robert-H on 2010-03-04
I'm getting the same problem with the same printer under CUPS on Lucid. It was working fine until about a week ago. I'm guessing that some upgrade messed it up. There seem to be thick black strips between paragraphs (and one page was half full of just black). It's the same whether I print from Ubuntu or Windows so the problem must be the code on the cups server.

---

### Post by Azdour on 2010-03-04
Hi,

We've been having this problem for more than a month now so I'm not sure if it was an upgrade that caused our problem.

---

### Post by kbs16355 on 2010-09-22
I have also been getting a similar problem with, yes you guessed it, an HP CM1312 running networked. It must indeed have been a buggy upgrade to the CUPS. In fact I think I saw an upgrade going through just before the issue appeared.

---

