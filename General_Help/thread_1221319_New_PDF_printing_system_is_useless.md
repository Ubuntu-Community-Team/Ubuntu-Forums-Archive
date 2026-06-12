---
title: "New PDF printing system is useless"
date: 2009-07-23
forum: General Help
---

### Post by FeraTech on 2009-07-23
Ok so I thought I would give the new PDF printing system a try. 

The CUPS-PDF package no longer works after the last update.

1. In the old system all you had to do was select PDF and printing meant you instantly get a PDF in your PDF folder. Very easy. The new system adds so many unnecessary steps.

2. Printing certain pictures causes the pdf to get corrupted and you can't print it at all. This was never a problem with CUPS-PDF.

3. New system no longer creates text searchable PDFs. So for businesses this is useless. You can's highlight or select text. This might be only for certain programs but at least this is what happens in Thunderbird.

---

### Post by lswb on 2009-07-23
I am using cups-pdf without trouble on 9.04. Note it must be separately installed. From synaptic, search for "cups-pdf" and mark/install or from terminal "sudo apt-get install cups-pdf" After installation both "Print to File" and PDF will be in your printer selections in the print dialog.

---

### Post by FeraTech on 2009-07-23
After the last CUPS update I get the following error:
/usr/lib/cups/backend/cups-pdf failed

I have gone through all the possible solutions with no results. The only option I have is the default PDF "print to file" feature. Which seems like it should be far from being the default option.

---

### Post by lswb on 2009-07-23
Here's a few threads that might help:

[http://ubuntuforums.org/showthread.php?t=1002573](http://ubuntuforums.org/showthread.php?t=1002573)

[https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/295536](https://bugs.launchpad.net/ubuntu/+source/cups-pdf/+bug/295536)

---

### Post by kaibob on 2009-07-23
Post deleted by Kaibob

---

### Post by FeraTech on 2009-07-24
For those interested. I spent 3 days trying to figure it out. I have no idea why this happened. I have 4 Ubuntu machines and my main desktop is the only one that developed this problem.

Figures it's the main PC I use for document management.

I fixed the issues with the following command:

```
sudo aa-complain cupsd
```

That is it. I still get "stopped with status 5!" errors in the cups-pdf logs but at least it works.

---

