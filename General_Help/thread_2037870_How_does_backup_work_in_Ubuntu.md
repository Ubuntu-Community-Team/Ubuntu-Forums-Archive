---
title: "How does backup work in Ubuntu?"
date: 2012-08-05
forum: General Help
---

### Post by urbaindepuce on 2012-08-05
Hello, 

I just switched from Windows 7 to Ubuntu. First thing I noticed is that there is no backup program to create a system image I can easily restore in case of failure. In Windows 7 there are two options for backup; creating a system image or file -based backup. The cool thing is that when creating a system image you can use this image to restore the previous state of the system. In Ubuntu most of the backup software only copies and compresses all my files. Is that sufficient for restoring my whole system like all programs and settings like they were two days ago? I am confused on how backing up the system regularly and incremental does work on linux. I mean when I only have an archive with all my files I only could extract it to a location. On a windows system this would not work, because there is the registry for example. Just copying files could be not sufficient for restoring the state of my computer.

Thanks for your help.

---

### Post by cortman on 2012-08-05
Use [remastersys]("http://www.remastersys.com/") to create system image files.
AFA backup, there are numerous tools. I have used deja dup with moderate success. See [here]("https://www.google.com/search?q=backup+programs+ubuntu") for info...

---

### Post by HermanAB on 2012-08-05
+1 for DejaDup.

The Linux backup strategy is different.  Windows is expensive and difficult to install, therefore it makes sense to backup the whole house of cards.  Linux costs nothing and is easy to install, so when your HDD fails, it is better to install the latest Linux version, rather than try to recover an old tired version from backup.

Therefore, just use DejaDup to backup your data and forget about backing up the system, since it is rather pointless and a waste of time.

---

### Post by urbaindepuce on 2012-08-07
Thank you. DejaDup and Back in Time sound promising.

---

### Post by d4m1r on 2012-08-07
+1 for Deja Dup! Should be installed with 12.04 by default...However, AFAIK, it does backup only individual files/directories and does NOT create an entire bootable system image...

---

