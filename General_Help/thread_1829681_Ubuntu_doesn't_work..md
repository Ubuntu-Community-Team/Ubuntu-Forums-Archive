---
title: "Ubuntu doesn't work."
date: 2011-08-20
forum: General Help
---

### Post by speedruntrainer on 2011-08-20
Hello.

I have this problem for months but never asked for it.
When I startup Ubuntu it says lots of text.

[http://www.mediafire.com/?bznzqlaaquzb1pb](http://www.mediafire.com/?bznzqlaaquzb1pb)

Sorry for the too much shaking with the cam but that's how I am but it's viewable.

Thanks.

---

### Post by Basher101 on 2011-08-20
please provide more info. What pc do you have? (brand and model) What ubuntu did you install? Did it work on the Live CD? Did it work on the first bootup right after the install?

---

### Post by speedruntrainer on 2011-08-20
Well, I think I did something else wrong, because it was installed already.
I remember I did something with a new video driver because of that bug on 11.04 that it shows a blank screen when opening more windows.

Anyway, my PC specs:

AMD Athlon(tm) 64 X2 Dual Core Processor 3800+ 2.00Ghz
RAM: 1GB
nvidia GEForce 6150 LE

I'm using Windows Vista right now.

---

### Post by Basher101 on 2011-08-20
then that caused your issue. Ubuntu only "breaks" if you break it. it wont on itself. The best choice you have right now is reinstalling it. Or you are able to delete the driver and replace it with the old one using the Live CD, but this should be alot harder than doing a fresh install over your damaged ubuntu.

---

### Post by hasardeur on 2011-08-20
If I saw correctly then the Stopping of the automatic Crash Report Generation failed. That is non fatal. Are you able to boot to Gnome or is the machine "stuck" at the promt?

---

### Post by Basher101 on 2011-08-20
I also get the error on the automatic crash report generation failing. The thing is, it NEVER cancelled my plymouth at bootup, i have only seen it on shutdown..

---

### Post by speedruntrainer on 2011-08-20
I'm going reinstall it, downloading right now because I don't know where the CD is at the moment.

This will take a hour.

---

### Post by speedruntrainer on 2011-08-21
Ok, so, I found my CD finally. (My PC didn't read a blank CD I used)

So, how to remove the other Ubuntu I have on my Harddrive or how to install over it?

---

### Post by adrien214 on 2011-08-22
> **Basher101 said:**
> ...Ubuntu only "breaks" if you break it. it wont on itself. ...

I cannot second this opinion.

As for reinstalling, boot from the CD and when you will get to the partioner, simply check the "format" box for the partition holding your current broken ubuntu installation and select "/" mounting option for this partition. (depending on which version of ubuntu we are speaking about, you need to select the manual option for partitioning. If you have dual boot win/linux, don't touch any partition that read "ntfs" or "fat32".

---

### Post by speedruntrainer on 2011-08-22
Already solved it myself removing the partition using Windows.
Then I reinstalled Ubuntu 10.04 LTS, I'll use that for a while.

Everything is working again, thanks :)

---

