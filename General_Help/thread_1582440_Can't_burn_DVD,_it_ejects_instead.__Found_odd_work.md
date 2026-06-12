---
title: "Can't burn DVD, it ejects instead.  Found odd workaround."
date: 2010-09-26
forum: General Help
---

### Post by Chymist on 2010-09-26
I recently upgraded from Hardy to Lucid.  I can read data and video DVDs, but when I tried to burn one from an .iso image file with Brasero, it started the burn, then ejected the disk and gave me an error message.  Here is the error log:  

I switched to Gnomebaker and had the same problem.  I went into the Gnomebaker preferences and unchecked the eject option and checked the Force option.  When I tried the burn, I got an error message but the disk didn't eject.  i tried the burn again and it worked!  If I go through the first error I can make Gnomebaker burn both data DVDs and burn from image files.  When I tried to change preferences in Brasero, there was no eject option.

I am using exactly the same hardware that worked fine in Hardy with the same bland DVD+R disks.  Brasero worked in Hardy.

Given the workaround, it doesn't appear to be a hardware, firmware, or driver problem.  Can anyone help shed some light on this?  Could it be a configuration file held over from Hardy that is causing this?

---

### Post by andrewthomas on 2010-09-26
I would purge all the brasero files and then reinstall them.

---

### Post by Chymist on 2010-09-26
I purged Brasero and Wodim and reinstalled them.  I had never installed Gnomebaker before this.  That didn't fix the problem.

---

### Post by andrewthomas on 2010-09-27
try and remove the ~/.config/brasero/ directory and then purge and reinstall again

---

### Post by Chymist on 2010-09-27
OK, I tried removing ~/.config/braero, purging brasero and reinstalling.  Brasero still ejects the blank disk right after it starts the burn.

Now another strange thing:  I can burn a data CD in the same drive using Brasero without a hitch.  I tried the data disk on my internal CD drive and it reads it just fine.

---

