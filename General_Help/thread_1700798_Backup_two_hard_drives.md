---
title: "Backup two hard drives"
date: 2011-03-05
forum: General Help
---

### Post by mkstallings1 on 2011-03-05
My laptop has two hard drives.  The first runs Windows XP SP3, and the second runs Ubuntu 10.10.  I wouls like to image both of them without having to run Clonezilla once on the first hard drive and then again on the second.  I would like to have software that I can tell to image both drives and create two images.  Any ideas?  I don't have to use Clonezilla. I have recently started playing around with Paragon Backup as well,and I really like it, especially the fact that you can run it from a live disk like Clonezilla.

---

### Post by psusi on 2011-03-05
I am pretty sure you can do this with clonezilla; you just need to give it the command line options telling it what to image rather than using the gui.

---

### Post by mkstallings1 on 2011-03-05
I guess I'll play around with it a little as that is a bit intimidating to me, but what is the worst that can happen?  That is what backups are for.

---

### Post by seawolf167 on 2011-03-05
> **psusi said:**
> I am pretty sure you can do this with clonezilla; you just need to give it the command line options telling it what to image rather than using the gui.

This is probably the way to go - run through the GUI, select your settings to image your first hard drive, then right before it starts the actual imaging process it gives you the command line output. Something like "the command line options to run this image again is *'something something something'*".

Write that down, then rerun Clonezilla but select the command line option on boot and modify the given line to include another hard drive.

---

### Post by mkstallings1 on 2011-03-05
Thanks!  I'll give that a try and see what happens.

---

### Post by jbiggs12 on 2011-03-06
You can always try using tar instead of clonezilla for your backups, although it's commandline-only and not as user-friendly. See this guide:

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

All you'd have to do is open up two separate terminal windows, both backing up the different drives.

---

