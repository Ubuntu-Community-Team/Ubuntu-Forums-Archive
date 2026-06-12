---
title: "Printer not printing"
date: 2012-05-14
forum: General Help
---

### Post by frisket on 2012-05-14
I just did a clean install of 12.04 on my Dell Optiplex 755 and it's all working nicely except for printing. I have a HP OfficeJet Pro K8600 and it was detected at install time, but when I print, the printer light blinks but the job just sits in the queue and nothing ever gets printed.

The printer was working fine under 10.04 with hplip an hour before, so I installed a fresh HPLIP from HP's web site, deleted the discovered printer and added it afresh. Same problem.

The CUPS access_log shows the test file being sent to the printer OK:

```
localhost - - [14/May/2012:13:07:14 +0100] "POST /printers/Officejet_Pro_K8600 HTTP/1.1" 200 424 Print-Job successful-ok
```

but the error_log keeps on saying:

```
D [14/May/2012:13:17:12 +0100] cupsdSetBusyState: newbusy="Printing jobs and dirty files", busy="Active clients, printing jobs, and dirty files"
```

and then it cycles through:

```
I [14/May/2012:13:17:43 +0100] Saving subscriptions.conf...
D [14/May/2012:13:17:44 +0100] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs and dirty files"
D [14/May/2012:13:22:13 +0100] Closing client 16 after 300 seconds of inactivity...
D [14/May/2012:13:22:13 +0100] cupsdCloseClient: 16
D [14/May/2012:13:22:13 +0100] cupsdSetBusyState: newbusy="Printing jobs", busy="Printing jobs"
D [14/May/2012:13:22:13 +0100] Report: clients=0
D [14/May/2012:13:22:13 +0100] Report: jobs=4
D [14/May/2012:13:22:13 +0100] Report: jobs-active=1
D [14/May/2012:13:22:13 +0100] Report: printers=1
D [14/May/2012:13:22:13 +0100] Report: printers-implicit=0
D [14/May/2012:13:22:13 +0100] Report: stringpool-string-count=22499
D [14/May/2012:13:22:13 +0100] Report: stringpool-alloc-bytes=13096
D [14/May/2012:13:22:13 +0100] Report: stringpool-total-bytes=416368

```

but nothing ever prints.

Where should I start looking?

---

### Post by CrusaderAD on 2012-05-14
I had a similar problem and discovered it was the format of the file I was printing. The printer wouldn't process it. Try testing with something like a plain txt file to see if it's the file you're attempting to print.

---

### Post by frisket on 2012-05-14
> **CerealCypher said:**
> I had a similar problem and discovered it was the format of the file I was printing. The printer wouldn't process it. Try testing with something like a plain txt file to see if it's the file you're attempting to print.
All I have tried so far is the built-in test page from the CUPS web interface and the Printer application. I haven't tried printing a file of my own yet. If it can't print its own test page, it's broken.

---

### Post by frisket on 2012-05-15
Oh duuh. One of the cartridges was out of ink. Replacing it fixed things.

So WTF doesn't the log file fscking well say so, HP?

---

### Post by CrusaderAD on 2012-05-15
Sometimes the simplest things throw us a curveball. Happens to us all.

---

