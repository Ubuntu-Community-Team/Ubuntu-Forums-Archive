---
title: "Help with Printing Issues"
date: 2010-07-01
forum: General Help
---

### Post by ngrieb on 2010-07-01
Hi, I have an HP 6300 printer and am attempting to use it in conjunction with my Netbook, which is running Ubuntu 9.10. The problem is that when printing I often can't print more than one page at a time before the printer just falls silent. It almost seems like the print buffer doesn't continue asking for the next page to print after the first is finished. Can anyone help me with this issue? Thanks.

---

### Post by ngrieb on 2010-07-24
Seems as though the printer was set as shared, and nor enabled somehow. At least this is what it seems to be in 10.04 after I upgraded. A few problems are fixed, but some more are added. Yay.

---

### Post by sgosnell on 2010-07-24
I'm not sure exactly what you meant by the last sentence.  I have a 6300, and it works fine.  I have it connected to my router, for use by any computer on my home network.  It prints, scans, and faxes without any problems.

---

### Post by ngrieb on 2010-07-30
I thought I had fixed this issue but it came back again. What happens is that when I start a printing job, after a certain period of time the printer disables itself...i.e. the little check next to the "enabled" in the printer config goes away, which stops the print job right in the middle of printing. I want to ask if there is a file that contains the printer config. ? Would making this file read only solve the constant disabling of the printer? 

sgosnell: it works at scanning and printing etc., but not fully. Printouts look fine, but stopping in the middle of a document is an issue and a waste of paper and ink. What version of Ubuntu are you using? This is under 10.04 now, and was happening under 9.10 while I had it too.

Thanks.

---

### Post by sgosnell on 2010-07-30
I'm currently using 10.04, but I've printed successfully with every version since 8.04.  I've never seen the occurrences you mention, so I have no idea what could be causing it.

---

### Post by HunterA3 on 2010-07-31
I've had nearly the exact same thing happen with my 10.04
What's odd is that it did work at one time, now it disables itself immediately after telling the printer to print. Even after re-enabling it, it disables the printer and errors out.

---

### Post by HunterA3 on 2010-08-02
Think I got it figured out (at least on my machine).  Had to set the printer to AppSocket/JetDirect network printer via DNS-SD. It had been set on IPP Network Printer via DNS-SD. No more issues with the printer resetting the enabled status. :D

---

### Post by ngrieb on 2010-08-04
Um, ok. Sounds like a printer networking issue, but I'm really only attempting to plug directly into the printer and print. I have no idea what this printer is set up for because I didn't set it up. Can you step me through what I would need to do, cause networking is something I have just barely started looking at.

---

### Post by drdos2006 on 2010-08-04
What happens when you type : [http://localhost:631/](http://localhost:631/)
Are you able to access the CUPS setup ?

regards

---

### Post by ngrieb on 2010-08-04
Yes, I see the CUPS setup. Not sure if I fixed it (until the next 10 page print I need to make), but I found the network settings inside the printer settings toolbox. Are you using the HPIPL driver or the CUPS driver?

---

