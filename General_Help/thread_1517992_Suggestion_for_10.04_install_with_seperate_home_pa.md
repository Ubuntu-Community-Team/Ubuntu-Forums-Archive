---
title: "Suggestion for 10.04 install with seperate /home partition"
date: 2010-06-25
forum: General Help
---

### Post by lsutiger on 2010-06-25
I currently am running 9.04 and tried to install 10.04 because I had some file system issues with the / partition. Instead of spending hours troubleshooting that, I decided to just try the latest flavor, 10.04.

Well, I had a lot of issues! One was  could not get compiz working. The other was that the ATI driver would not load correctly. After a reboot, I lost networking.
I posted about some of the problems but did not get much response. One that I did get was to clear out all of my settings folders (hidden folders in the /home folder).

Now I have been on Ubuntu since 6.04. Sure I had a problem here and there, but always found a solution within a reasonable time. I have always had my /home folder on a separate partition and never had problems like the ones I posted above.

Could the settings in my home folder really be the cause for the video driver not working correctly? Could it be the settings in the .compiz folder caused such problems?

PS - I really liked 10.04's speed!!! WOW!!!

BTW - The specs for the laptop in question: ATI Radeon Xpress 200m, AMD Turion X2, 2GB DDR2 (shared with video)


Just asking....BTW I went ahead and pulled the 9.04 cd out and installed...had my system up and running (with all of my customizations) in less than 2 hours.

Makes me wonder if 10.04 was rushed through production and put out before it was ready for prime time....just my 2 cents.

But I would like to know if anybody here thinks what I was told could be the problem.

Thanx

---

### Post by ubunterooster on 2010-06-25
I have deleted the .compiz folder when I borked stuff once. You could try removing the folder (or renaming so if that is not it you can name it back to what it was) and rebooting before you decide the only solution to be a reinstallation

---

### Post by dcstar on 2010-06-25
> **lsutiger said:**
> I currently am running 9.04 and tried to install 10.04 because I had some file system issues with the / partition. Instead of spending hours troubleshooting that, I decided to just try the latest flavor, 10.04.

Well, I had a lot of issues! One was  could not get compiz working. The other was that the ATI driver would not load correctly. After a reboot, I lost networking.
I posted about some of the problems but did not get much response. One that I did get was to clear out all of my settings folders (hidden folders in the /home folder).
........

Old configuration files in /home from earlier releases can cause issues.

Create a new user, log into it and see what happens.

---

### Post by lsutiger on 2010-06-25
Thank you for the quick replies. I will run rsync tonight and start in the a.m. with the new install, minus the .settings folder.

Will let you know!

---

### Post by lsutiger on 2010-06-28
OK - backed up everything, deleted all configuration folders in the /home/me/ folder (ie .config). 
Installed with / and /home on separate partitions. Went a little smoother this time. I have compiz working but can not get emerald to work.
I receive the following error:```
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
compiz (core) - Warn: Exceeded max texture size

Launching fallback window manager
```

---

### Post by lsutiger on 2010-06-28
OK compiz and emerald are working after update! YAY!
Really liking 10.04 so far..couple of annoyances, but I am sure I'll find a solution here somewhere.

Thanx for your input!

---

### Post by ubunterooster on 2010-06-28
Congrats!

---

