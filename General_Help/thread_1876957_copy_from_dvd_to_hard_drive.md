---
title: "copy from dvd to hard drive"
date: 2011-11-07
forum: General Help
---

### Post by brotell on 2011-11-07
Hi all I am having trouble at the moment I would like to transfer some of my dvd's to my 2 TB hard drive I do not need to shrink them can anyone give me a way to go I am using 10.04 LTS..

Thanks in advance 

Terry

---

### Post by crazy bird on 2011-11-07
Can't you just select the files from the DVD and drag them to you 2 TB drive? I think it's just a matter of drag and drop...
 
Or did you try this already?

---

### Post by brotell on 2011-11-07
Tried it already no go

---

### Post by crazy bird on 2011-11-07
> **brotell said:**
> Tried it already no go
 
Do you own permissions on your 2 TB disc? Meaning, can you read/write to it under your login?

---

### Post by lynrock on 2011-11-07
If you mean feature film dvds try K9copy. It is a Qt app and will pull in some KDE dependencies but it is very straight forward to use. It will rip dvds and keep the original structure (and menus and subtitles). It can also compile the files into an iso for burning to a disk, but if you just want blayback from you hard drive you can omit this step.

---

### Post by ppv on 2011-11-07
What happens when you drag and drop. Is your disk mounted.
 
Open Nautilus. Press F3. Click on one pane and then click on DVD in the left most pane. Then click on the other pane and click on your disk in the left most pane. This should show you the contents of both the dvd and the disk in the two panes. Now try to drag and drop from the DVD pane to the Disk pane.

---

### Post by andrew.46 on 2011-11-08
Perhaps the easiest way is to use vobcopy, make sure you have libdvdcss installed if the dvds are encrypted. Syntax to simply mirror the dvd is:

```
vobcopy -m
```

---

