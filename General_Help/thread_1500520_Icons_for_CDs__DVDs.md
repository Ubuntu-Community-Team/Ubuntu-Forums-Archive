---
title: "Icons for CDs / DVDs"
date: 2010-06-03
forum: General Help
---

### Post by winjeel on 2010-06-03
For windows computers, you make an "autorun" file and point it to the icon.ico file, and when the disk is inserted, you get the icon of your choice displayed. However, how do I make a similar set up for Linux?

---

### Post by labinnsw on 2010-06-04
Shouldn't that be autorun.inf for Windows?

Give your icon the name "favicon.ico" and place it in the root directory of the Pen drive.

Also save a text file similar to the one below as autorun. 

```
#!/bin/sh
/media/KINGSTON/StartPortableApps.exe
```

---

### Post by winjeel on 2010-06-04
Yes, autorun.inf, but for CDs and DVDs it's icon.ico (favicon is for web sites, I thought). So, that code in an autorun.inf file, and favicon.ico will be fine for CDs and DVDs for linux? If I wanted to have the icon work for both Windows and Linux, I assumed I'd need to different files with different file names (not two called autorun.inf for Windows and autorun.inf for Linux).

---

### Post by labinnsw on 2010-06-05
I have no idea why I am giving instructions for USB drives. Any way 
1.   favincon.ico works on Pen drives.  
2.   The script is only necessary if you want to autorun an application
3.   Any *.ico file in the root directory will do the job.

This is an example of a Linux User and Developer autorun file used to open an html with one or other of a variety of applications:```
#!/bin/sh
firefox index.html || mozilla-firefox index.html || mozilla index.html || konqueror index.html || opera index.html
```

The icon was call cdrom.ico

---

### Post by winjeel on 2010-06-05
Thanks for the help

> **labinnsw said:**
> ...
3.   Any *.ico file in the root directory will do the job.

...The icon was call cdrom.ico

This is perhaps what I'm looking for. However, the *.ico (of course with a real file name in place of the asterix) hadn't been doing anything in Linux, which is why I asked this question. I'll try the cdrom.ico... but dvdrom.ico? (I need to backup a several Gig's of images).

---

