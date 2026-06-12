---
title: "Problems With CD/DVD Drive"
date: 2010-08-28
forum: General Help
---

### Post by donato roque on 2010-08-28
I was trying to burn an iso image downloaded to my hard drive.  So I fed a blank cd disk into the cd drive, check.  Then opened nautilus and went to the directory where I downloaded the iso image.  Right clicked the file and chose Write to disc...

A pop-up window tells me to replace the disc.  By the way all other options in that pop-up window is grayed-out.

Additionally, the load averages goes up to 6.50 and beyond.  All other application is frozen.  I can't even shutdown the computer.  I had to do a hard shutdown.  Power off switch.  I've never done that for a very long time.  Not with Linux.

Is this a bug with cd burning?  I can't do anything with the cd/dvd drive.

Thank you.

---

### Post by DavePlummer on 2010-08-28
I believe that your problem is caused by a persisten bug in Brasero. I have had the same problem on multiple machines. I even confirmed tha the problem persists in Maverick Meerkat. To work around the problem, I installed GnomeBaker from the repositories. After I confirmed that GnomeBaker worked for me, I removed Brasero, the default CD/DVD burning application in Gnome.

---

### Post by donato roque on 2010-08-28
Thanks DavePlummer,

I do remember about a bug with Brasero.  But the last time I burn an iso image with this machine was right after I installed Ubuntu 10.04, around May 2010 and I finished that task without any problems.  I still have my Lucid Lynx backup iso here. 

I don't understand what changed between that fresh install and now.  

I tried gnomebaker but it did not work either.  Whatever the problem is its not the individual application that's causing this.

---

