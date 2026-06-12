---
title: "Can play avi file on DVD but can't copy it"
date: 2009-09-23
forum: General Help
---

### Post by c-roc on 2009-09-23
I have a bunch of DVDs (of avi files) that are probably a few years old. they've been sitting in a booklet all that time (most probably burnt with windows at full speed). I knew they wouldn't all work now, but a frustratingly large number won't copy onto my ubuntu desktop.  
However, I just noticed that the last one I tried, happened to play perfectly fine all the way through off the DVD.  I tried to copy to desktop again, and I immediately get an error. "Error reading from file: Input/output error"
Other files on the DVD copied ok.

Is there some sort of 'compatibility mode' or 'good enough for an avi, ignore minor errors' mode of copying I can use?

thanx.

---

### Post by yabbadabbadont on 2009-09-23
That is strange.  It plays fine, but you get I/O errors when trying to copy it.  If it still plays fine, even after you got the errors, you could try slowing down the drive to see if it would work then.  You can use the 'eject' command line tool to set the drive speed.  You need to have the disc in the drive, and the speed setting is lost any time you eject a disc.  On my machine, the dvd drive is /dev/scd0, so the command to set it to 1X speed would be: ```
sudo eject -x 1 /dev/scd0
```  I'm not sure if the sudo is needed, but it won't hurt to use it.

---

### Post by mc4man on 2009-09-23
you could also try using dvdisaster, with these being data disks you won't have to worry about drive authentication (needed for comm. dvd movies

```
sudo apt-get install dvdisaster
```

The first time you run you'll see pop up in screenie, ck. the box and click "Skip R502 Test"

Then just make sure your drive is correct in upper left panel and click the 'read' button in upper right side panel

The first run should be left at the default of 1 read try per sector.

Depending on how many unreadable sectors and the ability of your drive to resume speed after read errors the first run may be time consuming.

After it's done you can continue with multiple runs, **only the missed sectors will be attempted on further runs.** (saves time, any additional recovered sectors will be added to the .iso

I'd then set the read tries to maybe 5 for the 2nd run, if more runs are needed then up the tries. (some data may never be recovered

The read tries, ect settings are accessed from that little 'tool' icon.
dvdisaster will be found in applications -> system tools

Leve the "skip 16 sectors" setting alone for dvd media

(note that many of the settings are also links to a help file if you want to read.

---

### Post by c-roc on 2009-09-24
looks like that dvdisaster will the do the trick.  thanx!

---

