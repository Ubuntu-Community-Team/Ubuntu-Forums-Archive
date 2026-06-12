---
title: "start a program after Ubuntu has found all drives"
date: 2010-07-12
forum: General Help
---

### Post by Tom_ZeCat on 2010-07-12
It's a long story, but on my tri-boot (Ubuntu 8.04, Win 7, Win XP), both Win 7 and Win XP need to know that Linux has previously run.  I've therefore written a little program in REALbasic that automatically creates a text file named linuxran.txt and puts it into the root folder of the partition where Windows XP is installed.  Under Ubuntu, this location is known as "/media/Win XP".  It's an 80 gig partition of a 1 TB drive, the same disk that Win 7 is installed on.  In my partition app under Win 7, I labeled the partition "Win XP."  

The good news: When Ubuntu is completely up and running, the program runs fine.  It checks if the file already exists, and if it does not, it creates it.  So in Ubuntu, under System ==> Preferences ==> Sessions ==> Startup Programs, I put my little program, figuring it would run just fine.  The bad news: Unfortunately, it didn't.  It's trying to start before Ubuntu has mounted the "/media/Win XP" drive/partition.  

Possible solutions: 1. If I could somehow set my program to run after I know the other drive has loaded, I would be all right.  I know the prog is fine once the drive is loaded, because it does what it's supposed to when I run it.  Is there some way to put my app in the startup process after Ubuntu has mounted all the drives?  2. Put some code in my app to make Ubuntu mount that drive before the rest of the prog runs.  Not sure if this one is practical.  3. Set the program to run, not when Ubuntu first starts up, but rather, right before it shuts down.  

I like option #3 the best because it would require no re-coding.  Ubuntu would have had plenty of time to mount all the drives.  Is there some way to tell Ubuntu, "whenever you're told to shut down, always run this little program first?"

---

### Post by chessnerd on 2010-07-12
Might be relevent to you:

[http://ubuntuforums.org/showthread.php?t=1278619](http://ubuntuforums.org/showthread.php?t=1278619)

I'm not good with scripting. I barely know anything about it, but this seems to discuss different ways to run a script at shutdown...

---

### Post by Tom_ZeCat on 2010-07-12
Thanks.  That's valuable info and I checked it out.  However, now I realize that running my app just before shut-down won't necessarily help.  I was assuming that Ubuntu automatically mounted all drives after boot-up.  Turns out, this seems not to be true.  

I recoded my program to wait 3 minutes before saving the file to the hard drive where Win 7 and XP are installed.  I got the same program error as before.  However, when I made sure to click on the drive with Ubuntu's file explorer, the drive mounted, then when the 3 minute timer triggered my app to run, it ran fine.  

What I need to do is recode the program to check if the drive is mounted and then, if it's not, mount the drive.  I'm going to ask the question on the REALbasic programming forum.  However, REALbasic is primarily used by Macintosh programmers.  Most of them have little to do with Linux.  I think I need to find a Linux-based programming forum, especially one that discusses some form of BASIC.  If they know how to mount a drive in another form of BASIC, that might give me clues on how to do it in realBASIC.  Or I could write the app in the other type of BASIC.

---

### Post by JustinR on 2010-07-12
I didn't read this whole thread but why not just use /etc/fstab to mount all of the drives on bootup?

---

