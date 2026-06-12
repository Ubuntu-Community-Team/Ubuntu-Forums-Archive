---
title: "diagnosing boot problems"
date: 2010-06-21
forum: General Help
---

### Post by poldie on 2010-06-21
Recently my machine hung during boot.  Trial and error (I didn't receive any help here!) got it working - I loaded up an older kernel using grub, reinstalled my graphics driver, then rebooted into the latest kernel, and reinstalled the driver again and now it seems to be working.

But I need to be able to fix these sorts of problems for myself.  How do I go about working out how far into the boot process I got, from log files or anything else?  I can see a lot of log files and they seem to be missing date/time stamps.  Some have dates mentioned in the contents of the file, and some you can access through the log viewer which lets you pick a data, but mostly they have some sort of offset which increments...sometimes.

---

### Post by ajgreeny on 2010-06-21
If you mean the *name*.log.2.gz increasing to *name*.log.4.gz, that is just an archive of other log files, so don't worry.

---

### Post by poldie on 2010-06-21
> **ajgreeny said:**
> If you mean the *name*.log.2.gz increasing to *name*.log.4.gz, that is just an archive of other log files, so don't worry.

More generally - the problem is, my machine was hanging on a black screen during boot.  The question is - where do I look to see what was happening; what the last successful event was; what it failed on.  On windows you just have an Application, or System, or Security event log.  On ubuntu there are loads, and they have numbers like:

0.000000000012  

as the first parameter, so it looks sort of like some sort of elapsed time, but it's not terrible useful for working out what happened and when.

---

### Post by wilee-nilee on 2010-06-21
Could be anything, but I suspect a graphic card driver,
if you boot and are getting a black screen. When you boot hit the shift key, at the grub choice hit e then use the arrow keys to get to the end of the kernel add nomodset and remove the splash, hlod down ctrl and hit x to boot from there. nomodset is a low graphic mode login and is only per session.
If you need to know the graphic card in the terminal.
```
lspci | grep VGA
```
Look for the driver in synaptic. You might post the card for us to see.

---

