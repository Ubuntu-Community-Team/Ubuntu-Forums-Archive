---
title: "Minor speed performance issues"
date: 2010-05-29
forum: General Help
---

### Post by jereece on 2010-05-29
I have been using Ubuntu for about 10 months and just recently upgraded to 10.4. In general Ubuntu's speed performance is good but I have noted a couple minor performance issues in both releases compared to Windows XP.  I would like to see if anyone is aware of any known issues or fixes. I dual boot Win XP SP3 and Ubuntu 10.4.

1) Images displayed in Evolution email notes are very slow to render compared to Microsoft Outlook.  I would estimate that Outlook renders images from the same source / email 3 or 4 times faster.

2) When closing Firefox, it takes a full 7 seconds to actually close once I click the close button.  Firefox on Win XP closes almost instantaneously but let's say about 1 second. 

Any help with these issues are appreciated.

Jim

---

### Post by ibuclaw on 2010-05-29
> **jereece said:**
> I have been using Ubuntu for about 10 months and just recently upgraded to 10.4. In general Ubuntu's speed performance is good but I have noted a couple minor performance issues in both releases compared to Windows XP.  I would like to see if anyone is aware of any known issues or fixes. I dual boot Win XP SP3 and Ubuntu 10.4.

1) Images displayed in Evolution email notes are very slow to render compared to Microsoft Outlook.  I would estimate that Outlook renders images from the same source / email 3 or 4 times faster.

2) When closing Firefox, it takes a full 7 seconds to actually close once I click the close button.  Firefox on Win XP closes almost instantaneously but let's say about 1 second. 

Any help with these issues are appreciated.

Jim

1) Is a known bug with Evolution, it's not a speed issue. It's that Evolution opens and closes a new connection for each image it retrieves.

2) How many tabs do you have open when you close firefox? And what filesystem are you using? Mount options? Sounds like you have lots of data in cache, and when you close firefox, it rushes to write all data to disk before closing the application.

3) Windows XP was released 10 years ago, Ubuntu 10.04 was released last month. Windows was made to run on systems with 64MB RAM minimal, Ubuntu 256MB minimal. Try not to compare sticks and stones, it will get you nowhere fast. ;)

---

### Post by lavinog on 2010-05-29
for the firefox issue:
bleachbit has a feature that speeds up firefox called vacuum. It rebuilds the database that firefox uses which can get full of garbage over time.

Also a fresh install of 10.04 seems to have a performance benefit over an upgrade.  Upgrading from ext3 to ext4 doesn't give the full benefit of ext4...creating a new partition can help sometimes.

There are some tutorials on the forums for optimizing firefox.
You might want to give chromium a try.  It is a lot (if not a million times) faster.

---

### Post by jerenept on 2010-05-29
tsk tsk... Chromium.
Try Konqueror of Epiphany if you want speed. They both use a similar KHTML/WebKit rendering engine.
If you're ok with using a beta program, Midori is very fast  browser with lots of cool features.

XP can run on 64MB RAM? My neighbour has a Duron 900MHz with 128MB and XP barely runs.

---

### Post by lavinog on 2010-05-29
> **jerenept said:**
> 
XP can run on 64MB RAM? My neighbour has a Duron 900MHz with 128MB and XP barely runs.
It can, but it is really slow.  The recent service packs have bloated it up quite a bit so I don't know about running sp3 with 64m.

---

### Post by jereece on 2010-05-29
Thanks for letting me know that the issue with Evolution is a known issue.  

The issue with Firefox is even when I only have one tab open.  As far as file system and mount options, I don't have a clue what you are talking about.  Whatever comes standard with Ubuntu 32bit is what I am using.  I have used Chrome and it's okay but I like FF better.  I will try Konqueror.

Sorry if I hurt anyones feelings with the comparison to WinXP.  I was only comparing the 2 OS I am currently running.  WinXP however will not run well on anything less than 512meg of RAM however.  I am running 2gig however in my desktop, so I don't think RAM is an issue.

I appreciate your help.
Jim

---

