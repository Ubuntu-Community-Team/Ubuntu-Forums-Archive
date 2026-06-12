---
title: "Chromium thinks PDF's are dangerous"
date: 2010-12-13
forum: General Help
---

### Post by thebarisaxkid on 2010-12-13
I know, it's really weird.  Chromium version 8.0.552.215 in Ubuntu 10.10 is thinking that PDF files are dangerous.  

```
This type of file may harm your computer.  Download anyway? (Yes/No)
```

I don't need this fixed immediately, as it is only a minor annoyance.

I know my sources of the PDF's so I know that they don't have any malware attached.

---

### Post by ean5533 on 2010-12-13
PDFs **are** dangerous, and Chromium is right to give you that warning. There have been many, many exploits showing up the last couple years that come in through read-only PDFs that can completely compromise your system. Granted, 99% of these exploits are Windows-specific and wouldn't hurt your Linux machine, but that doesn't mean PDFs are necessarily safe.

So, don't expect a "fix" for this to come out, because it isn't a bug; rather, it's a feature specifically coded by chromium developers. Unless they add a flag to chromium's settings to turn off that warning, it isn't going to go away.

Besides, all you have to do is click "yes".

---

### Post by ghlargh on 2010-12-14
I use my computer for work, before this "fix" was added to chromium i was able to click on a PDF link and it would automatically open the file after downloading.

Now i have to click the link, click OK, wait for the download, click the tab at the bottom again to open the file and then close the download bar... This gets annoying after 30 or 40 times.

---

### Post by Chris_82 on 2010-12-14
I think the issue got more or less solved [as can be seen here (issue 65895)]("http://code.google.com/p/chromium/issues/detail?id=65895").
So the new version should not show this dialog anymore.
PDFs and other files remain being potentially dangerous.


cheers.

---

### Post by xintera. on 2010-12-14
I don't think its dangerous,its only a matter of info/harm pop-up which comes from Chromium because its still in development.

---

### Post by thebarisaxkid on 2010-12-22
> Now i have to click the link, click OK, wait for the download, click the tab at the bottom again to open the file and then close the download bar... This gets annoying after 30 or 40 times. 
Agreed, it does become annoying.
 
I understand that pdf's *can* be dangerous, but so can anything else.  Theoretically, evything that can be downloaded is *potentially* dangerous.
 
As I always say, if it can be written, malware can be written for it.

---

